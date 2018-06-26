---
title: 將拖放： 實作置放目標 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33088477c579cbdfe48140b806c6376b520e470c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928914"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>拖放：實作置放目標
本文概述如何讓您的應用程式的置放目標。 實作置放目標需要稍微多一些工作會比實作置放來源，但是它仍然相當簡單。 這些技術也適用於非 OLE 應用程式。  
  
#### <a name="to-implement-a-drop-target"></a>若要實作置放目標  
  
1.  將成員變數加入至您想要的置放目標的應用程式中的每個檢視。 這個成員變數必須屬於型別`COleDropTarget`或從其衍生的類別。  
  
2.  從您的檢視類別函式會處理**WM_CREATE**訊息 (通常`OnCreate`)，呼叫新的成員變數`Register`成員函式。 `Revoke` 將會自動呼叫您在檢視時終結。  
  
3.  覆寫下列函式。 如果您想在應用程式的相同的行為，會覆寫檢視類別中的這些函式。 如果您想要修改在隔離狀況中的行為，或想要啟用拖放上非`CView`windows 中，覆寫這些函式，在您`COleDropTarget`-衍生的類別。  
  
    |覆寫|若要允許|  
    |--------------|--------------|  
    |`OnDragEnter`|卸除作業才會發生在視窗中。 當游標第一次進入視窗時呼叫。|  
    |`OnDragLeave`|當拖曳作業離開指定的視窗的特殊行為。|  
    |`OnDragOver`|卸除作業才會發生在視窗中。 當資料指標拖曳至橫跨視窗時呼叫。|  
    |`OnDrop`|正在卸除到指定的視窗的資料處理。|  
    |`OnScrollBy`|捲動時所需的目標視窗中的特殊行為。|  
  
 請參閱 MAINVIEW。CPP 檔案，MFC OLE 範例的一部分[OCLIENT](../visual-cpp-samples.md)如需這些函式如何一起運作的範例。  
  
 如需詳細資訊，請參閱:  
  
-   [實作置放來源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [建立和終結 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [管理 OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>另請參閱  
 [拖放 (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget 類別](../mfc/reference/coledroptarget-class.md)
