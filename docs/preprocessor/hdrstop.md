---
title: "hdrstop | Microsoft Docs"
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
  - "hdrstop_CPP"
  - "vc-pragma.hdrstop"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "hdrstop pragma"
  - "Pragma, hdrstop"
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hdrstop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

讓您對先行編譯檔案名稱，以及儲存編譯狀態之位置進行其他控制。  
  
## 語法  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## 備註  
 *filename* 是要使用或建立之先行編譯標頭檔的名稱 \(取決於是否指定 [\/Yu](../build/reference/yu-use-precompiled-header-file.md) 或 [\/Yc](../build/reference/yc-create-precompiled-header-file.md)\)。  如果 *filename* 不包含路徑規格，則會假設先行編譯的標頭檔位於與原始程式檔案相同的目錄。  
  
 如果 C 或 C\+\+ 檔案包含 **hdrstop** pragma，當使用 \/Yc 編譯時，編譯器儲存編譯狀態的位置取決於 pragma 的位置。  pragma 後方任何程式碼的編譯狀態都不會儲存。  
  
 使用 *filename* 為要儲存編譯狀態的先行編譯標頭檔命名。  **hdrstop** 和 *filename* 之間的空格是選擇性的。  在 **hdrstop** pragma 中指定的檔案名稱是一個字串，因此會受到任何 C 或 C\+\+ 字串條件約束的限制。  請特別注意，您必須使用引號將其括住，以及使用逸出字元 \(反斜線\) 來指定目錄名稱。  例如：  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 先行編譯標頭檔的名稱是根據下列規則來決定的，依照優先順序列出：  
  
1.  \/Fp 編譯器選項的引數。  
  
2.  \#**pragma hdrstop** 的 *filename* 引數  
  
3.  原始程式檔副檔名為 .PCH 的主檔名。  
  
 對於 \/Yc 和 \/Yu 選項，如果兩個編輯選項和 **hdrstop** pragma 中都未指定檔案名稱，則會使用原始程式檔的主檔名做為先行編譯標頭檔的主檔名。  
  
 您也可以使用前置處理命令來執行巨集取代，如下所示：  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 下列規則用於管理可放置 **hdrstop** pragma 的位置：  
  
-   它必須出現在所有資料或函式宣告或定義的外部。  
  
-   且必須在原始程式檔中，而不在標頭檔中指定。  
  
## 範例  
  
```  
#include <windows.h>                 // Include several files  
#include "myhdr.h"  
  
__inline Disp( char *szToDisplay )   // Define an inline function  
{  
    ...                              // Some code to display string  
}  
#pragma hdrstop  
```  
  
 在此範例中，**hdrstop** pragma 出現在兩個已包含及已定義內嵌函式的檔案之後。  一開始可能無法理解為什麼要在這個位置放置 pragma。  不過，考量到會使用手動先行編譯選項 \/Yc 和 \/Yu，因此使用 **hdrstop** pragma 可讓您先行編譯整個原始程式檔 \(包括內嵌程式碼\)。  Microsoft 編譯器並不會限制您只先行編譯資料宣告。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)