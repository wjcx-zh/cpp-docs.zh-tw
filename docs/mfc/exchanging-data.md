---
title: 交換資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 504d2ff9f011770f75db73a63fa77b821281269b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435554"
---
# <a name="exchanging-data"></a>交換資料

如同大多數對話方塊，在屬性工作表和應用程式之間的資料交換，是屬性工作表的其中一個最重要的函式。 本文說明如何完成這項工作。

使用屬性工作表交換資料實際上，是與屬性工作表之個別屬性頁交換資料的問題。 與屬性頁交換資料的程序是因為交換 對話方塊中，使用資料一樣[CPropertyPage](../mfc/reference/cpropertypage-class.md)物件是只是特製化[CDialog](../mfc/reference/cdialog-class.md)物件。 此程序會利用架構的對話資料交換 (Dialog Data Exchange，DDX) 機制，在對話方塊中的控制項和對話方塊物件的成員變數之間交換資料。

與屬性工作表交換資料和與一般對話方塊交換資料之間的重要差異為屬性工作表具有多個頁面，因此，您必須與屬性工作表中的所有屬性頁交換資料。 如需有關 DDX 的詳細資訊，請參閱 < [ 對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。

下列範例說明如何在檢視和屬性工作表的兩個頁面之間交換資料：

[!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]

## <a name="see-also"></a>另請參閱

[屬性工作表](../mfc/property-sheets-mfc.md)

