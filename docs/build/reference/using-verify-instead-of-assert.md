---
title: "使用 VERIFY 取代 ASSERT | Microsoft Docs"
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
  - "assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASSERT 陳述式"
  - "判斷提示, 偵錯"
  - "判斷提示, 疑難排解 ASSERT 陳述式"
  - "偵錯 [MFC], ASSERT 陳述式"
  - "偵錯判斷提示"
  - "VERIFY 巨集"
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 VERIFY 取代 ASSERT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

假設當您執行 MFC 應用程式的偵錯版本時沒有任何問題。  然而，同一個應用程式的發行組建卻損毀、傳回不正確的結果，和 \(或\) 出現其他某些不正常的行為。  
  
 這個問題可能是因為您將重要的程式碼置於 ASSERT 陳述式中以驗證是否正確執行而導致的。  由於在 MFC 程式的發行組建中將 ASSERT 陳述式設成註解，因此該程式碼在發行的組建中無法執行。  
  
 如果您要使用 ASSERT 確認函式呼叫 \(Function Call\) 是否成功，請考慮改用 [VERIFY](../Topic/VERIFY.md)。  VERIFY 巨集會在應用程式的偵錯版和發行的組建中都評估其自己的引數。  
  
 另一個建議的方法是，將函式的傳回值指派為暫存變數，然後測試 ASSERT 陳述式中的變數。  
  
 檢查下列程式碼片段：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 這組程式碼在 MFC 應用程式的偵錯版中執行無誤。  如果呼叫 `calloc( )` 失敗，包含檔案和行號的診斷訊息便會出現。  不過，在 MFC 應用程式的零售版中：  
  
-   從未呼叫 `calloc( )`、保持 `buf` 未初始化，或  
  
-   `strcpy_s( )`將 "`Hello, World`"  複製到記憶體的隨機區段，可能會損毀應用程式或導致系統停止回應，或  
  
-   `free()` 會嘗試釋放從未配置的記憶體。  
  
 若要正確使用 ASSERT，程式碼範例應改成如下所示：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 或者，您可改用 VERIFY：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## 請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)