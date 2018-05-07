---
title: CReBar vs。CReBarCtrl |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6d0b8df40676cc64c97a6bdef013321c404899f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crebar-vs-crebarctrl"></a>CReBar vs。CReBarCtrl
MFC 提供兩個類別來建立 rebar: [CReBar](../mfc/reference/crebar-class.md)和[CReBarCtrl](../mfc/reference/crebarctrl-class.md) （包裝 Windows 通用控制項 API）。 **CReBar**提供所有 rebar 通用控制項的功能，也可以為您處理許多必要的通用控制項設定和結構。  
  
 如果您不想要整合 Rebar MFC 架構，`CReBarCtrl` 是 Win32 Rebar 控制項的包裝函式類別，因此可能會更容易實作。 如果您計劃使用 `CReBarCtrl` 並整合 Rebar 到 MFC 架構中，您必須另花心思將 Rebar 控制項操作傳達至 MFC。 這種通訊並不困難。不過，它是額外的工作，當您使用時，就不需要**CReBar**。  
  
 Visual C++ 提供兩種利用 Rebar 通用控制項的方式。  
  
-   建立 rebar 使用**CReBar**，然後呼叫[crebar:: Getrebarctrl](../mfc/reference/crebar-class.md#getrebarctrl)存取`CReBarCtrl`成員函式。  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 為內嵌成員函式轉換**這**rebar 物件指標。 這表示在執行階段的函式呼叫沒有額外負荷。  
  
-   建立 rebar 使用[CReBarCtrl](../mfc/reference/crebarctrl-class.md)的建構函式。  
  
 任何一個方法都可讓您存取 Rebar 控制項的成員函式。 當您呼叫 `CReBar::GetReBarCtrl`時，會傳回 `CReBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 請參閱[CReBar](../mfc/reference/crebar-class.md)建構和建立 rebar，使用如**CReBar**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

