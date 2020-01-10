---
title: 哪裡可以找到訊息對應
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: c50c6fc1134f579859530972dc864103c4e0ebcf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907362"
---
# <a name="where-to-find-message-maps"></a>哪裡可以找到訊息對應

當您使用 [應用程式精靈] 建立新的基本架構應用程式時，應用程式精靈會針對它為您建立的每個命令目標類別，寫入訊息對應。 這包括您的衍生應用程式、檔、視圖和框架視窗類別。 其中有些訊息對應已有應用程式 Wizard 針對特定訊息和預先定義的命令所提供的專案，而有些則只是您將新增之處理常式的預留位置。

類別的訊息對應位於。類別的 CPP 檔案。 使用應用程式精靈所建立的基本訊息對應，您可以使用[類別 Wizard](reference/mfc-class-wizard.md)來新增每個類別將處理之訊息和命令的專案。 在您新增一些專案之後，一般訊息對應可能如下所示：

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

訊息對應是由宏的集合所組成。 兩個宏[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)和[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)，並括住訊息對應。 其他宏（例如`ON_COMMAND`）則填入訊息對應的內容。

> [!NOTE]
>  訊息對應宏後面不接分號。

當您使用 [加入類別] wizard 建立新的類別時，它會提供類別的訊息對應。 或者，您也可以使用原始程式碼編輯器來手動建立訊息對應。

## <a name="see-also"></a>另請參閱

[架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)
