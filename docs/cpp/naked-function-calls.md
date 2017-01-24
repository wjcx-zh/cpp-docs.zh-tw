---
title: "Naked 函式呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "終解程式碼"
  - "naked 函式"
  - "naked 關鍵字 [C++]"
  - "naked 關鍵字 [C++], 儲存類別屬性"
  - "初構程式碼"
  - "虛擬裝置驅動程式"
  - "虛擬裝置驅動程式, naked 函式呼叫"
  - "VXD 虛擬裝置驅動程式"
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Naked 函式呼叫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 使用 `naked` 屬性宣告的函式發出時不會包含初構和終解程式碼，如此您就可以使用[內嵌組合語言](../assembler/inline/inline-assembler.md)撰寫自訂初構\/終解序列。  Naked 函式是做為進階功能提供。  這些函式可讓您宣告從 C\/C\+\+ 以外的內容呼叫的函式，因此對於參數位置以及要保留哪些暫存器會做出不同的假設。  範例包括像是中斷處理常式這類常式。  這項功能對於虛擬裝置驅動程式 \(VxD\) 的撰寫者特別實用。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Naked 函式的規則和限制](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [撰寫初構\/終解程式碼的考量](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
### END Microsoft 特定的  
  
## 請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)