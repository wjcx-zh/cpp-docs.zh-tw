---
title: "一般 MBCS 程式設計的建議 | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "對話方塊 [C++], 字型"
  - "MBCS [C++], 對話方塊字型"
  - "MBCS [C++], 程式設計"
  - "MS Shell Dlg"
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 一般 MBCS 程式設計的建議
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   為了方便日後的調整，請盡量使用例如 `_tcschr` 和 `_tcscpy` 的執行階段巨集。  如需詳細資訊，請參閱 [TCHAR.H 裡泛用文字的對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   使用 C 執行階段 `_getmbcp` 函式來取得目前字碼頁的相關資訊。  
  
-   不要重新使用字串資源。  根據目標語言而定，指定的字串在轉譯時可能有不同的意義。  例如，應用程式的主功能表上的「檔案」可以與對話方塊裡的「檔案」有不同的轉譯。  如果您需要使用一個以上含相同名稱的字串，為每一個使用不同的字串識別項。  
  
-   您可能會想知道應用程式是否執行於啟用 MBCS 的作業系統。  若要實行，在程式啟動時設定旗標；不要依賴 API 呼叫。  
  
-   在設計對話方塊的時候，請在靜態文字控制項的結尾允許大約 30% 的額外空間，以供 MBCS 轉譯使用。  
  
-   當為您的應用程式選擇字型時請小心，因為有些字型無法在所有的系統上使用。  例如，Windows 2000 的日文版不支援 Helvetica 字型。  
  
-   選取對話方塊的字型時，請使用 [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112)，而不要使用 MS Sans Serif 或 Helvetica。  系統會在建立對話方塊之前，以正確的字型取代 MS Shell Dlg。  使用 MS Shell Dlg 可確保作業系統對這個字型所作的任何變更都會自動地成為可用狀態 \(由於 Windows 95、Windows 98 和 Windows NT 4 無法正確處理 MS Shell Dlg，所以 MFC 會將 MS Shell Dlg 取代成 DEFAULT\_GUI\_FONT 或系統字型\)。  
  
-   設計應用程式時，請決定哪個字串可以當地語系化。  如果有懷疑，假設任何給定字串都會本土化。  因此，不要將可本土化的字串和不能本土化的字串混合。  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)