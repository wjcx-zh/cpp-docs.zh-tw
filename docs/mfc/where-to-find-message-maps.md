---
title: 哪裡可以找到訊息對應
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: d9b9a50062334822f34047b8e22e67541ccaa952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217854"
---
# <a name="where-to-find-message-maps"></a>哪裡可以找到訊息對應

當您使用應用程式精靈建立新的基本架構應用程式時，應用程式精靈 會為您撰寫的訊息對應，它會建立每個命令目標類別。 這包括衍生的應用程式、 文件、 檢視和框架視窗類別。 這些訊息對應部分已經有特定的訊息和預先定義的命令，應用程式精靈所提供的項目，有些則只是預留位置，您將加入的處理常式。

類別的訊息對應位於。類別的 CPP 檔案。 您可使用應用程式精靈建立基本的訊息對應，將訊息和命令處理每個類別的項目加入使用 [屬性] 視窗。 新增一些項目之後，一般的訊息對應可能如下所示：

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

訊息對應巨集的集合所組成。 兩個巨集， [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)並[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)，括住的訊息對應。 其他巨集，例如`ON_COMMAND`，填入訊息對應的內容。

> [!NOTE]
>  訊息對應巨集的之後不會以分號隔開。

當您使用 [加入類別精靈] 來建立新的類別時，它會提供類別的訊息對應。 或者，您可以建立使用原始程式碼編輯器，以手動方式的訊息對應。

## <a name="see-also"></a>另請參閱

[架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)
