---
title: Funktionsweise des lokalen Prozesses mit Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Beschreibt die Prozesse zum Verwenden des lokalen Prozesses mit Kubernetes zum Herstellen einer Verbindung zwischen Ihrem Entwicklungscomputer und Ihrem Kubernetes-Cluster
keywords: Lokaler Prozess mit Kubernetes, Docker, Kubernetes, Azure, Container
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 5b6c07d5987c52d818a35babd16681652ddf5830
ms.sourcegitcommit: 50bbb62525c91c5a31bab57e1caf37c5638872c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87913261"
---
# <a name="how-local-process-with-kubernetes-works"></a>Funktionsweise des lokalen Prozesses mit Kubernetes

Der lokale Prozess mit Kubernetes ermöglicht Ihnen das Ausführen und Debuggen von Code auf Ihrem Entwicklungscomputer, während der Kubernetes-Cluster weiterhin mit den übrigen Anwendungen oder Diensten verbunden ist. Wenn Sie z. B. über eine umfangreiche Microservicearchitektur mit einer Vielzahl von Diensten und Datenbanken verfügen, die voneinander abhängig sind, kann es schwierig sein, diese Abhängigkeiten auf Ihrem Entwicklungscomputer zu replizieren. Außerdem kann der Vorgang zum Erstellen und Bereitstellen von Code in Ihrem Kubernetes-Cluster für jede Codeänderung während der Inner Loop-Entwicklung langsam, zeitaufwendig und bei Verwendung mit einem Debugger wenig benutzerfreundlich sein.

Bei Verwendung des lokalen Prozesses mit Kubernetes muss Ihr Code nicht erstellt und im Cluster bereitgestellt werden. Stattdessen wird eine direkte Verbindung zwischen Ihrem Entwicklungscomputer und Ihrem Cluster hergestellt. Indem Sie Ihren Entwicklungscomputer während des Debuggens mit Ihrem Cluster verbinden, können Sie Ihren Dienst im Handumdrehen im Kontext der gesamten Anwendung testen und entwickeln, ohne dazu eine Docker- oder Kubernetes-Konfiguration erstellen zu müssen.

Wenn Sie den lokalen Prozess mit Kubernetes verwenden, wird Datenverkehr zwischen Ihrem verbundenen Kubernetes-Cluster und Ihrem Entwicklungscomputer umgeleitet. Diese Umleitung des Datenverkehrs ermöglicht es, dass Code auf dem Entwicklungscomputer und die im Kubernetes-Cluster ausgeführten Dienste so kommunizieren, als befänden sie sich im gleichen Kubernetes-Cluster. Der lokale Prozess bietet außerdem die Möglichkeit, die für Pods im Kubernetes-Cluster verfügbaren Umgebungsvariablen und bereitgestellten Volumes auf dem Entwicklungscomputer zu replizieren. Indem Sie auf Ihrem Entwicklungscomputer auf Umgebungsvariablen und bereitgestellte Volumes zugreifen können, können Sie Ihren Code rasch bearbeiten, ohne diese Abhängigkeiten manuell replizieren zu müssen.

> [!WARNING]
> Der lokale Prozess für Kubernetes ist nur für die Verwendung in Entwicklungs- und Testszenarien vorgesehen. Er ist nicht für den Einsatz in Produktionsclustern oder Livediensten konzipiert und wird dort nicht unterstützt.

## <a name="using-local-process-with-kubernetes"></a>Verwenden des lokalen Prozesses mit Kubernetes

Zur Verwendung eines lokalen Prozesses mit Kubernetes in Visual Studio benötigen Sie eine unter Windows 10 ausgeführte Instanz der [Visual Studio 2019][visual-studio]-Version 16.7 Preview 4 oder höher, für die die Workload *ASP.NET und Webentwicklung* sowie die [Kubernetes-Erweiterung für lokale Prozesse][lpk-extension] installiert ist. Wenn Sie den lokalen Prozess mit Kubernetes verwenden, um eine Verbindung zu Ihrem Kubernetes-Cluster herzustellen, haben Sie die Möglichkeit, den gesamten Datenverkehr zu und von einem vorhandenen Pod im Cluster auf Ihren Entwicklungscomputer umzuleiten.

> [!NOTE]
> Wenn Sie den lokalen Prozess mit Kubernetes verwenden, werden Sie aufgefordert, den Namen des Diensts einzugeben, der auf Ihren Entwicklungscomputer umgeleitet werden soll. Diese Option ist eine bequeme Möglichkeit, einen Pod für die Umleitung zu identifizieren. Alle Umleitungen zwischen Ihrem Kubernetes-Cluster und dem Entwicklungscomputer sind für einen Pod vorgesehen.

Wenn der lokale Prozess mit Kubernetes eine Verbindung mit Ihrem Cluster herstellt, geht er wie folgt vor:

* Fordert Sie auf, den auf Ihrem Cluster zu ersetzenden Dienst, den für Ihren Code zu verwendenden Port auf Ihrem Entwicklungscomputer und die Startaufgabe für Ihren Code als einmalige Aktion zu konfigurieren.
* Der Container im Pod im Cluster wird durch einen Remote-Agent-Container ersetzt, der Datenverkehr an Ihren Entwicklungscomputer umleitet.
* [kubectl port-forward][kubectl-port-forward] wird auf dem Entwicklungscomputer ausgeführt, um Datenverkehr vom Entwicklungscomputer an den Remote-Agent weiterzuleiten, der im Cluster ausgeführt wird.
* Es werden Umgebungsinformationen von Ihrem Cluster mithilfe des Remote-Agents erfasst. Zu diesen Umgebungsinformationen zählen Umgebungsvariablen, sichtbare Dienste, Volumeeinbindungen und Geheimniseinbindungen.
* Richten Sie die Umgebung in Visual Studio so ein, dass der Dienst auf Ihrem Entwicklungscomputer auf dieselben Variablen zugreifen kann, wie wenn er auf dem Cluster ausgeführt werden würde.  
* Die Hostdatei wird aktualisiert, um Dienste auf Ihrem Cluster lokalen IP-Adressen auf dem Entwicklungscomputer zuzuordnen. Diese Hostdateieinträge ermöglichen, dass Code, der auf dem Entwicklungscomputer ausgeführt wird, Anforderungen an andere Dienste senden kann, die in Ihrem Cluster ausgeführt werden. Um die Hostdatei zu aktualisieren, fordert der lokale Prozess mit Kubernetes beim Herstellen einer Verbindung mit Ihrem Cluster Administratorzugriff auf dem Entwicklungscomputer an.
* Startet die Ausführung und das Debuggen Ihres Codes auf Ihrem Entwicklungscomputer. Falls erforderlich, gibt der lokale Prozess mit Kubernetes erforderliche Ports auf Ihrem Entwicklungscomputer frei, indem er Dienste oder Prozesse beendet, die diese Ports derzeit verwenden.

Nachdem Sie eine Verbindung mit Ihrem Cluster hergestellt haben, können Sie Code ohne Containerisierung nativ auf Ihrem Computer ausführen und debuggen, und der Code kann direkt mit dem Rest Ihres Clusters interagieren. Sämtlicher Netzwerkverkehr, den der Remote-Agent empfängt, wird an den während der Verbindung angegebenen lokalen Port umgeleitet, sodass der nativ ausgeführte Code diesen Datenverkehr akzeptieren und verarbeiten kann. Die Umgebungsvariablen, Volumes und Geheimnisse aus dem Cluster werden für Code zur Verfügung gestellt, der auf dem Entwicklungscomputer ausgeführt wird. Aufgrund der Hostdateieinträge und der Portweiterleitung, die auf dem Entwicklercomputer durch den lokalen Prozess mit Kubernetes hinzugefügt wurden, kann Ihr Code außerdem Netzwerkdatenverkehr an Dienste senden, die in Ihrem Cluster ausgeführt werden. Dabei werden die Dienstnamen aus dem Cluster verwendet, und dieser Datenverkehr wird an die Dienste weitergeleitet, die in Ihrem Cluster ausgeführt werden. Der Datenverkehr wird zwischen dem Entwicklungscomputer und Ihrem Cluster weitergeleitet, solange die Verbindung besteht.

Darüber hinaus bietet der lokale Prozess mit Kubernetes eine Möglichkeit, Umgebungsvariablen und eingebundene Dateien, die für Pods in Ihrem Cluster auf Ihrem Entwicklungscomputer verfügbar sind, über die Datei `KubernetesLocalProcessConfig.yaml` zu replizieren. Sie können diese Datei auch verwenden, um neue Umgebungsvariablen und Volumeeinbindungen zu erstellen.

> [!NOTE]
> Für die Dauer der Verbindung mit dem Cluster (plus weitere 15 Minuten) führt der lokale Prozess mit Kubernetes auf Ihrem lokalen Computer einen Prozess namens *EndpointManager* mit Administratorrechten aus.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Zusätzliche Konfiguration mit KubernetesLocalProcessConfig.yaml

Mit der Datei `KubernetesLocalProcessConfig.yaml` können Sie Umgebungsvariablen und eingebundene Dateien replizieren, die für Pods in Ihrem Cluster verfügbar sind. Weitere Informationen zu den zusätzlichen Konfigurationsoptionen finden Sie unter [Konfigurieren des lokalen Prozesses mit Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Verwenden von Routingfunktionen für die isolierte Entwicklung

Der lokale Prozess mit Kubernetes leitet den gesamten Datenverkehr standardmäßig für einen Dienst an Ihren Entwicklungscomputer um. Außerdem können Sie Routingfunktionen verwenden, um Anforderungen an einen Dienst von einer Unterdomäne an Ihren Entwicklungscomputer umzuleiten. Mithilfe dieser Routingfunktionen können Sie den lokalen Prozess mit Kubernetes verwenden, um Ihre Entwicklung isoliert durchzuführen und Unterbrechungen des anderen Datenverkehrs in Ihrem Cluster zu vermeiden.

In der folgenden Animation werden zwei Entwickler veranschaulicht, die isoliert auf demselben Cluster arbeiten:

![Animierte GIF zur Veranschaulichung der Isolierung](media/local-process-kubernetes/lpk-graphic-isolated.gif)

Wenn Sie die isolierte Entwicklung ermöglichen, führt der lokale Prozess mit Kubernetes zusätzlich zum Herstellen einer Verbindung mit Ihrem Kubernetes-Cluster Folgendes durch:

* Er überprüft, ob Azure Dev Spaces für den Kubernetes-Cluster aktiviert ist.
* Er repliziert Ihren ausgewählten Dienst im Cluster im gleichen Namespace und fügt die Bezeichnung *routing.visualstudio.io/route-from=SERVICE_NAME* und die Anmerkung *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* hinzu.
* Er konfiguriert und startet den Routing-Manager im gleichen Namespace auf dem Kubernetes-Cluster. Der Routing-Manager verwendet eine Bezeichnungsauswahl, um nach der Bezeichnung *routing.visualstudio.io/route-from=SERVICE_NAME* und der Anmerkung *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* zu suchen, wenn das Routing für Ihren Namespace konfiguriert wird.

Wenn der lokale Prozess mit Kubernetes ermittelt, dass Azure Dev Spaces auf Ihrem Kubernetes-Cluster aktiviert ist, werden Sie dazu aufgefordert, Azure Dev Spaces zu deaktivieren, bevor Sie den lokalen Prozess mit Kubernetes verwenden können.

Der Routing-Manager ergreift folgende Aktionen, wenn er gestartet wird:
* Er dupliziert alle Eingänge im Namespace mithilfe von *GENERATED_NAME* für die Unterdomäne. 
* Er erstellt einen Envoy-Pod für jeden Dienst, der einem duplizierten Eingang mit der Unterdomäne *GENERATED_NAME* zugeordnet ist.
* Er erstellt einen zusätzlichen Envoy-Pod für den Dienst, an dem Sie isoliert arbeiten. Dies ermöglicht das Weiterleiten von Anforderungen mit der Unterdomäne an Ihren Entwicklungscomputer.
* Er konfiguriert Routingregeln für jeden Envoy-Pod, um das Routing für Dienste mit der Unterdomäne zu verarbeiten.

Wenn eine Anforderung mit der Unterdomäne *GENERATED_NAME* vom Cluster empfangen wird, wird der Header *kubernetes-route-as=GENERATED_NAME* zur Anforderung hinzugefügt. Die Envoy-Pods verarbeiten das Routing der Anforderung an den entsprechenden Dienst im Cluster. Wenn die Anforderung an den Dienst weitergeleitet wird, der isoliert bearbeitet wird, wird diese Anforderung vom Remote-Agent an Ihren Entwicklungscomputer umgeleitet.

Wenn eine Anforderung ohne die Unterdomäne *GENERATED_NAME* vom Cluster empfangen wird, wird kein Header zur Anforderung hinzugefügt. Die Envoy-Pods verarbeiten das Routing der Anforderung an den entsprechenden Dienst im Cluster. Wenn die Anforderung an den Dienst weitergeleitet wird, der ersetzt wird, wird diese Anforderung an den ursprünglichen Dienst anstelle des Remote-Agents weitergeleitet.

> [!IMPORTANT]
> Jeder Dienst auf Ihrem Cluster muss den Header *kubernetes-route-as=GENERATED_NAME* weiterleiten, wenn zusätzliche Anforderungen gestellt werden. Wenn *serviceA* beispielsweise eine Anforderung empfängt, wird eine Anforderung an *serviceB* gestellt, bevor eine Antwort zurückgegeben wird. In diesem Beispiel muss *serviceA* den Header *kubernetes-route-as=GENERATED_NAME* in der Anforderung an *serviceB* weiterleiten. Einige Sprachen, z. B. [ASP.NET][asp-net-header], verfügen möglicherweise über Methoden zum Verarbeiten der Headerweitergabe.

Wenn Sie die Verbindung mit Ihrem Cluster trennen, entfernt der lokale Prozess mit Kubernetes standardmäßig alle Envoy-Pods und den duplizierten Dienst. 

> [HINWEIS] Die Bereitstellung und der Dienst werden weiterhin in Ihrem Namespace ausgeführt. Führen Sie die folgenden Befehle für Ihren Namespace aus, um die Bereitstellung und den Dienst zu entfernen.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnose und Protokollierung

Wenn Sie den lokalen Prozess mit Kubernetes zum Herstellen einer Verbindung mit Ihrem Cluster verwenden, werden Diagnoseprotokolle Ihres Clusters auf dem Entwicklungscomputer im Ordner *Lokaler Prozess mit Kubernetes* im Verzeichnis *TEMP* protokolliert.

## <a name="limitations"></a>Einschränkungen

„Lokaler Prozess mit Kubernetes“ unterliegt folgenden Einschränkungen:

* „Lokaler Prozess mit Kubernetes“ leitet Datenverkehr für einen einzelnen Dienst an Ihren Entwicklungscomputer um. Sie können „Lokaler Prozess mit Kubernetes“ nicht verwenden, um mehrere Dienste gleichzeitig umzuleiten.
* Ein Dienst muss von einem einzelnen Pod unterstützt werden, um eine Verbindung mit diesem Dienst herzustellen. Sie können keine Verbindung mit einem Dienst mit mehreren Pods herstellen, z. B. einem Dienst mit Replikaten.
* In einem Pod darf nur ein einzelner Container ausgeführt werden, damit „Lokaler Prozess mit Kubernetes“ erfolgreich eine Verbindung herstellen kann. „Lokaler Prozess mit Kubernetes“ kann keine Verbindung mit Diensten mit Pods herstellen, die über zusätzliche Container verfügen, wie z. B. Sidecar-Container, die von Dienstgittermodellen eingefügt werden.
* „Lokaler Prozess mit Kubernetes“ benötigt erhöhte Rechte, damit er auf Ihrem Entwicklungscomputer ausgeführt werden kann, um Ihre Hostdatei zu bearbeiten.
* Der lokale Prozess mit Kubernetes kann nicht auf Clustern verwendet werden, auf denen Azure Dev Spaces aktiviert ist.

### <a name="local-process-with-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Lokaler Prozess mit Kubernetes und Cluster, auf denen Azure Dev Spaces aktiviert ist

Sie können den lokalen Prozess mit Kubernetes nicht auf Clustern verwenden, auf denen Azure Dev Spaces aktiviert ist. Wenn Sie den lokalen Prozess mit Kubernetes auf einem Cluster verwenden möchten, auf dem Azure Dev Spaces aktiviert ist, müssen Sie Azure Dev Spaces deaktivieren, bevor Sie eine Verbindung mit Ihrem Cluster herstellen.

## <a name="next-steps"></a>Nächste Schritte

Informationen zu den ersten Schritten bei der Verwendung des lokalen Prozesses mit Kubernetes zum Herstellen einer Verbindung zwischen Ihrem lokalen Entwicklungscomputer und Ihrem Cluster finden Sie unter [Verwenden des lokalen Prozesses mit Kubernetes (Vorschau)](local-process-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-local-process-with-kubernetes.md