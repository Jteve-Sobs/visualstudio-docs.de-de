---
title: 'Vorgehensweise: Verwalten mehrerer Threads in verwaltetem Code | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe5cef9f7aebcbfc93ffd057a109647e45b5967
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387069"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Gewusst wie: Verwalten mehrerer Threads in verwaltetem Code
Wenn Sie über eine verwaltete VSPackage-Erweiterung verfügen, die asynchrone Methoden aufruft oder Vorgänge ausführt, die auf anderen Threads als dem UI-Thread von Visual Studio ausgeführt werden, sollten Sie die unten aufgeführten Richtlinien befolgen. Sie können verhindern, dass der UI-Thread reaktionsfähig ist, weil er nicht auf den Abschluss der Arbeit in einem anderen Thread warten muss. Sie können Ihren Code effizienter gestalten, da Sie nicht über zusätzliche Threads verfügen, die Stapel Speicher beanspruchen, und Sie können die Zuverlässigkeit und das Debuggen vereinfachen, da Sie Deadlocks und nicht reagierenden Code vermeiden.

 Im Allgemeinen können Sie vom UI-Thread zu einem anderen Thread wechseln oder umgekehrt. Wenn die Methode zurückgibt, ist der aktuelle Thread der Thread, von dem er ursprünglich aufgerufen wurde.

> [!IMPORTANT]
> In den folgenden Richtlinien werden die APIs im- <xref:Microsoft.VisualStudio.Threading> Namespace verwendet, insbesondere die- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Sie können eine Instanz eines- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Objekts aus der- <xref:Microsoft.VisualStudio.Shell.ThreadHelper> Eigenschaft erhalten `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Wechseln vom UI-Thread zu einem Hintergrund Thread

1. Wenn Sie sich im UI-Thread befinden und asynchrone Arbeit an einem Hintergrund Thread ausführen möchten, verwenden Sie Folgendes `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Wenn Sie sich im UI-Thread befinden und beim Ausführen von Arbeit an einem Hintergrund Thread synchron blockieren möchten, verwenden Sie die- <xref:System.Threading.Tasks.TaskScheduler> Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Wechseln von einem Hintergrund Thread zum UI-Thread

1. Wenn Sie sich in einem Hintergrund Thread befinden und etwas im UI-Thread ausführen möchten, verwenden Sie Folgendes <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Sie können die- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Methode verwenden, um zum UI-Thread zu wechseln. Diese Methode sendet eine Meldung an den UI-Thread, wobei die aktuelle asynchrone Methode fortgesetzt wird. Außerdem kommuniziert Sie mit dem Rest des Threading Frameworks, um die korrekte Priorität festzulegen und Deadlocks zu vermeiden.

     Wenn die Hintergrund Thread Methode nicht asynchron ist und Sie Sie nicht asynchron machen können, können Sie die-Syntax weiterhin verwenden, um `await` zum UI-Thread zu wechseln, indem Sie die Arbeit mit umschließen <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , wie im folgenden Beispiel gezeigt:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
