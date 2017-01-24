---
title: "訊息方塊樣式 | Microsoft Docs"
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
  - "MB_ICONQUESTION"
  - "MB_ICONINFORMATION"
  - "MB_DEFBUTTON2"
  - "MB_YESNO"
  - "MB_OKCANCEL"
  - "MB_TASKMODAL"
  - "MB_ICONEXCLAMATION"
  - "MB_OK"
  - "MB_DEFBUTTON3"
  - "MB_YESNOCANCEL"
  - "MB_APPLMODAL"
  - "MB_RETRYCANCEL"
  - "MB_DEFBUTTON1"
  - "MB_ABORTRETRYIGNORE"
  - "MB_SYSTEMMODAL"
  - "MB_ICONSTOP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MB_ABORTRETRYIGNORE 常數"
  - "MB_APPLMODAL 常數"
  - "MB_DEFBUTTON1 常數"
  - "MB_DEFBUTTON2 常數"
  - "MB_DEFBUTTON3 常數"
  - "MB_ICONEXCLAMATION 常數"
  - "MB_ICONINFORMATION 常數"
  - "MB_ICONQUESTION 常數"
  - "MB_ICONSTOP 常數"
  - "MB_OK 常數"
  - "MB_OKCANCEL 常數"
  - "MB_RETRYCANCEL 常數"
  - "MB_SYSTEMMODAL 常數"
  - "MB_TASKMODAL 常數"
  - "MB_YESNO 常數"
  - "MB_YESNOCANCEL 常數"
  - "訊息方塊樣式"
ms.assetid: d87014c5-4ea4-4950-a27e-7bcdda67be7d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息方塊樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列訊息方塊樣式可供使用。  
  
## Message\_Box 型別  
  
-   **MB\_ABORTRETRYIGNORE** 訊息方塊包含三個按鈕:中止、重試和忽略。  
  
-   **MB\_OK** 訊息方塊包含一個按鈕:好。  
  
-   **MB\_OKCANCEL** 訊息方塊包含兩個按鈕:確定和取消。  
  
-   **MB\_RETRYCANCEL** 訊息方塊包含兩個按鈕:重試和取消。  
  
-   **MB\_YESNO** 訊息方塊包含兩個按鈕:不是和。  
  
-   **MB\_YESNOCANCEL** 訊息方塊包含三個按鈕:是，而和取消。  
  
## 訊息方塊強制  
  
-   使用者必須回應訊息方塊在繼續在目前視窗的工作之前**MB\_APPLMODAL**。  不過，使用者在這些視窗移至視窗其他應用程式和工作。  如果 **MB\_SYSTEMMODAL** 和 **MB\_TASKMODAL** 都沒有指定，預設值為 **MB\_APPLMODAL** 。  
  
-   **MB\_SYSTEMMODAL** 所有應用程式暫停，直到使用者回應訊息方塊。  系統強制回應訊息方塊用來告知要求直接顧慮，應該謹慎使用嚴重，可能有害的錯誤。  
  
-   **MB\_TASKMODAL** 和 **MB\_APPLMODAL**相似，不過，不適合在 MFC 應用程式內。  這個旗標為沒有視窗控制代碼可用的呼叫的應用程式或程式庫是保留的。  
  
## 訊息方塊圖示  
  
-   **MB\_ICONEXCLAMATION** 驚嘆號點圖示會顯示在訊息方塊中。  
  
-   **MB\_ICONINFORMATION** 圖示包括「I」圓形會出現訊息方塊。  
  
-   **MB\_ICONQUESTION** 的問題標記圖示會顯示在訊息方塊中。  
  
-   **MB\_ICONSTOP** 會中止標記圖示會顯示在訊息方塊中。  
  
## 訊息方塊的預設按鈕。  
  
-   **MB\_DEFBUTTON1** 第一個按鈕是預設值。  請注意第一個按鈕永遠是預設，除非 **MB\_DEFBUTTON2** 和 **MB\_DEFBUTTON3** 指定。  
  
-   **MB\_DEFBUTTON2** 第二個按鈕是預設值。  
  
-   **MB\_DEFBUTTON3** 第三個按鈕是預設值。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)