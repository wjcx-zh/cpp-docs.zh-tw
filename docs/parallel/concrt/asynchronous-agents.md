---
title: 非同步代理程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e226a43358c8279b51a4f02849737c25554ccc5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377340"
---
# <a name="asynchronous-agents"></a>非同步代理程式

*非同步代理程式*(或簡稱*代理程式*) 是以非同步方式運作，來解決大型運算工作的其他代理程式的應用程式元件。 您可以將代理程式想成具有設定的生命週期的工作。 例如，一個代理程式可能會讀取的資料輸入/輸出裝置 （例如鍵盤、 磁碟上的檔案或網路連線） 和另一個代理程式可能會執行動作對該資料可供使用。 第一個代理程式會使用訊息傳遞通知的第二個代理程式詳細資料可供使用。 並行執行階段工作排程器提供有效率的機制，以啟用代理程式，以封鎖和相讓合作而不需要比較沒有效率的先佔。

此代理程式庫會定義[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)類別來代表非同步代理程式。 `agent` 是宣告虛擬方法的抽象類別[2&gt;concurrency::agent::run&lt;2}](reference/agent-class.md#run)。 `run`方法執行由代理程式所執行的工作。 因為`run`是抽象的您必須實作這個方法中的每個類別衍生自`agent`。

## <a name="agent-life-cycle"></a>代理程式生命週期

代理程式已設定的生命週期。 [Concurrency:: agent_status](reference/concurrency-namespace-enums.md#agent_status)列舉會定義代理程式的各種狀態。 下圖是顯示如何代理程式進行從某個狀態到另一個狀態圖表。 在此圖中，實線表示您從您的應用程式; 呼叫的方法虛線代表從執行階段呼叫的方法。

![代理程式狀態圖表](../../parallel/concrt/media/agentstate.png "agentstate")

下表描述中的每個狀態`agent_status`列舉型別。

|代理程式狀態|描述|
|-----------------|-----------------|
|`agent_created`|未排定執行代理程式。|
|`agent_runnable`|執行階段排程執行的代理程式。|
|`agent_started`|代理程式已啟動且正在執行。|
|`agent_done`|代理程式已完成。|
|`agent_canceled`|代理程式已取消之前進入`started`狀態。|

`agent_created` 是代理程式的初始狀態`agent_runnable`並`agent_started`都是作用中狀態，並`agent_done`和`agent_canceled`是終端機的狀態。

使用[concurrency::agent::status](reference/agent-class.md#status)方法來擷取目前的狀態`agent`物件。 雖然`status`是並行安全的方法，將代理程式狀態可以變更的時間`status`方法會傳回。 例如，代理程式可能處於`agent_started`狀態，當您呼叫`status`方法，但會移至`agent_done`後方狀態`status`方法會傳回。

## <a name="methods-and-features"></a>方法和功能

下表顯示一些重要的方法，屬於`agent`類別。 如需所有詳細資訊`agent`類別的方法，請參閱[代理程式類別](../../parallel/concrt/reference/agent-class.md)。

|方法|描述|
|------------|-----------------|
|[start](reference/agent-class.md#start)|排程`agent`執行的物件並將它設定為`agent_runnable`狀態。|
|[run](reference/agent-class.md#run)|執行所要執行的工作`agent`物件。|
|[完成](reference/agent-class.md#done)|移至代理程式`agent_done`狀態。|
|[[取消]](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|如果代理程式未啟動，這個方法會取消執行代理程式，並將它設定為`agent_canceled`狀態。|
|[status](reference/agent-class.md#status)|擷取目前的狀態`agent`物件。|
|[等候](reference/agent-class.md#wait)|等候`agent`物件以輸入`agent_done`或`agent_canceled`狀態。|
|[wait_for_all](reference/agent-class.md#wait_for_all)|等待所有提供`agent`輸入的物件`agent_done`或`agent_canceled`狀態。|
|[wait_for_one](reference/agent-class.md#wait_for_one)|等候至少其中一個提供`agent`輸入的物件`agent_done`或`agent_canceled`狀態。|

您建立代理程式物件之後，請呼叫[concurrency::agent::start](reference/agent-class.md#start)排程執行的方法。 執行階段會呼叫`run`方法之後其排程代理程式，並將它設定為`agent_runnable`狀態。

執行階段不會管理非同步代理程式所擲回的例外狀況。 如需有關例外狀況處理和代理程式的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

## <a name="example"></a>範例

如需示範如何建立基本的代理程式型應用程式的範例，請參閱 <<c0> [ 逐步解說： 建立代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)

