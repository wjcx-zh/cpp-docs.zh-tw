---
title: "說明功能表合併 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "功能表, 合併"
  - "合併說明功能表"
  - "說明, 針對主動式文件容器"
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 說明功能表合併
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當物件在容器內作用中， OLE 文件功能表合併通訊協定給物件 **Help** 功能表的控制權。  因此，除非使用者停用該物件，容器的說明主題無法使用。  現用文件內含項目結構在就地功能表合併的規則展開可以讓容器和是作用中的共用功能表的現用文件。  新規則是完全有關哪些元件的其他慣例擁有功能表的哪些部分，以及共用功能表如何建構。  
  
 新的慣例是簡單。  在現用文件， **Help** 功能表有組織的兩個最上層的功能表項目:  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 例如，當文字部分作用中的 Office 文件夾時，然後 **Help** 功能表會顯示如下:  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 兩個功能表項目底下的其他功能表項目特有的容器和物件提供給使用者的串聯功能表中。  哪些項目出現在這裡隨相關的容器和物件會有所不同。  
  
 要建構這個合併 **Help** 功能表，主動式文件內含項目結構修改標準 OLE 文件程序。  根據 OLE 文件，合併的功能表列可能有功能表，即 **File**， **Edit**， **Container**， `Object`， **視窗**， **Help**的六個群組，依此順序。  在每個群組中，可以有零或多個功能表。  群組、 **Container**和 **File 視窗** 屬於容器，而且群組 **Edit**和 **Object,** 和 **Help** 所屬的物件。  當物件要進行功能表合併時，它會建立一個空白的功能表列和傳遞至容器。  容器呼叫 **IOleInPlaceFrame::InsertMenus**然後插入其功能表。  物件也會通過六長度值的結構 \(**OLEMENUGROUPWIDTHS**\)。  在插入功能表之後，容器指示多少功能表在每一個加入它的群組，然後傳回。  然後物件在每個容器群組中插入其功能表，請注意計數功能表。  最後，可透過合併的功能表列和在每個群組中包含計數功能表\) 的陣列 \(如 OLE，傳回不透明「功能表描述元」控制代碼。  處理和合併的功能表列加入至容器後的物件傳遞，透過 **IOleInPlaceFrame::SetMenu**。  此時，容器顯示合併的功能表列也可透過控制代碼 OLE，因此， OLE 能讓功能表訊息適當的排程器。  
  
 在修改過的現用文件程序，物件必須先初始化 **OLEMENUGROUPWIDTHS** 元素為零再將它加入至容器。  然後容器執行一般功能表插入有例外狀況:容器在 **OLEMENUGROUPWIDTHS** 陣列 \(即寬度 \[5\] 最後 \(第六\) 輸入插入 **Help** 功能表做為最後一個項目並儲存值為 1，則需物件的說明群組\)。  這個 **Help** 功能表如前所述僅會是子功能表的項目， 「**Container Help** \>」串聯功能表。  
  
 物件接著會執行其一般功能表插入程式碼，不過，在插入其 **Help** 功能表之前，先檢查 **OLEMENUGROUPWIDTHS** 陣列的第六個項目。  如果值為 1，而最後一個功能表的名稱是 **Help** \(或適當的當地語系化字串\)，則物件將其功能表 **Help** 當做容器的 **Help** 功能表項目的子功能表。  
  
 物件然後調整 **OLEMENUGROUPWIDTHS** 的第六個元素為零且會將第五個項目。  這個呼叫 **Help** OLE 功能表屬於容器，而且應該傳送該功能表 \(及其子功能表對應之功能表訊息至容器。  它是然後容器的責任轉送 `WM_INITMENUPOPUP`， **WM\_SELECT**、 **WM\_COMMAND**和 **Help** 屬於功能表物件的部分的其他功能表相關的訊息。  這可以使用 `WM_INITMENU` 清除呼叫容器的旗標使用者是否巡覽至物件的 **Help** 功能表。  容器並注意 `WM_MENUSELECT` 中所有項目的輸入或輸出容器中沒有將本身的 **Help** 功能表。  進入時，即表示使用者巡覽至物件的功能表，因此，容器「在物件說明功能表」設定旗標並使用該旗標狀態轉送所有 `WM_MENUSELECT`、 `WM_INITMENUPOPUP`和 **WM\_COMMAND** 訊息，以最小，加入至視窗。\(在結束時，容器清除旗標會處理這些訊息\)。容器應該為這些訊息會使用物件的 **IOleInPlaceActiveObejct::GetWindow** 函式傳回的視窗做為目的端。  
  
 如果物件偵測零在 **OLEMENUGROUPWIDTHS**的第六個元素，它是根據標準 OLE 文件規則執行。  這個程序包括參與 **Help** 功能表合併不的容器以及這些。  
  
 當物件在顯示前呼叫 **IOleInPlaceFrame::SetMenu**時，合併的功能表列，容器確認 **Help** 功能表是否有其他子功能表，除了此處插入容器。  如果是的話，容器在合併的功能表列把它的 **Help** 功能表中。  如果 **Help** 功能表沒有其他的子功能表，容器從合併的功能表列將移除其 **Help** 功能表。  這個程序包括參與 **Help** 功能表合併的物件以及這些不是。  
  
 最後，當到了反組譯碼功能表時，移除其他插入的功能表以外，物件移除插入的 **Help** 功能表。  當容器移除它的功能表，則會移除其 **Help** 功能表將它插入的其他功能表以外。  
  
## 請參閱  
 [主動式文件容器](../mfc/active-document-containers.md)