---
title: "Implementing a Window with CWindowImpl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 視窗"
  - "subclassing ATL window classes"
  - "superclassing, ATL"
  - "windows [C++], ATL"
  - "windows [C++], subclassing"
  - "windows [C++], superclassing"
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing a Window with CWindowImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要實作  視窗中，從 `CWindowImpl`衍生一個類別。  在衍生類別中，宣告的訊息對應 \(Message Map\) 和訊息處理常式函式。  您可以用下列三種不同的方法可以使用您的類別:  
  
-   [建立以新的視窗類別的視窗](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [Superclass 現有視窗類別](#_atl_superclassing_an_existing_windows_class)  
  
-   [子類別的現有 Windows](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 建立以新的視窗類別的視窗  
 `CWindowImpl` 包含 [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md) 巨集會宣告視窗類別的資訊。  這個巨集實作 `GetWndClassInfo` 函式，使用 [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 定義新的視窗類別的相關資訊。  當 `CWindowImpl::Create` 呼叫時，這個視窗類別的登錄，並建立新的視窗。  
  
> [!NOTE]
>  `CWindowImpl` 傳遞至 **NULL**`DECLARE_WND_CLASS` 巨集，表示 ATL 會產生視窗類別名稱。  若要指定您的名稱，請將字串傳遞至 `CWindowImpl`的 `DECLARE_WND_CLASS` 衍生類別。  
  
## 範例  
 以下實作會根據新的視窗類別的視窗類別的範例:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_1.h)]  
  
 若要建立視窗，請建立 `CMyWindow` 執行個體會呼叫方法 **建立** 。  
  
> [!NOTE]
>  若要覆寫預設的視窗將訊息類別，請將 `CWndClassInfo` 成員執行在衍生類別中 `GetWndClassInfo` 方法為適當的值。  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> 設定 Superclass 現有視窗類別  
 [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md) 巨集可讓您建立類別的 Superclass 現有視窗的視窗。  指定這個巨集會在您的 `CWindowImpl`衍生類別。  就像其他 ATL 視窗，訊息是訊息對應的處理。  
  
 當您使用 `DECLARE_WND_SUPERCLASS`，新的視窗類別會註冊。  這個新類別將與現有的類別以 `CWindowImpl::WindowProc` 指定，不過，取代視窗程序的相同 \(或以覆寫這個方法\) 的函式。  
  
## 範例  
 下列 Superclass 標準編譯類別與類別的範例:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_2.h)]  
  
 若要建立 Superclass 編輯視窗，請建立 `CMyEdit` 執行個體會呼叫方法 **建立** 。  
  
##  <a name="_atl_subclassing_an_existing_window"></a> 子類別化現有視窗  
 若要子類別化現有的視窗中，從 `CWindowImpl` 衍生類別並宣告的訊息對應，在兩個上述情況。  不過，請注意，如果您沒有指定任何視窗類別資訊，，因為您將子類別現有視窗。  
  
 而不是呼叫 **建立**，呼叫 `SubclassWindow` 再將控制代碼傳遞至您要為子類別的現有視窗中。  一旦視窗為子類別，則會使用 `CWindowImpl::WindowProc` \(或覆寫這個方法\) 的函式用來導向訊息至訊息對應。  若要中斷連結您的物件的子類別化視窗，請呼叫 `UnsubclassWindow`。  視窗的原始視窗程序就會還原。  
  
## 請參閱  
 [Implementing a Window](../atl/implementing-a-window.md)