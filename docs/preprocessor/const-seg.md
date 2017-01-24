---
title: "const_seg | Microsoft Docs"
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
  - "vc-pragma.const_seg"
  - "const_seg_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "const_seg pragma"
  - "Pragma, const_seg"
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# const_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 .obj 檔案中儲存 [const](../cpp/const-cpp.md) 變數的區段。  
  
## 語法  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 備註  
 在本主題中，「*區段*」\(Segment\) 和「*區段*」\(Section\) 這兩個詞的意義可互換。  
  
 OBJ 檔案可以使用 [dumpbin](../build/reference/dumpbin-command-line.md) 應用程式檢視。  .obj 檔案中 `const` 變數的預設區段是 .rdata。  某些 `const` 變數 \(例如純量\) 會自動內嵌於程式碼資料流中。  內嵌的程式碼不會出現在 .rdata 中。  
  
 定義必須在 `const_seg` 中進行動態初始化的物件時，會產生未定義的行為。  
  
 未包含參數的 `#pragma const_seg` 會將區段重設為 .rdata。  
  
 `push` \(選擇性\)  
 將記錄放置到內部編譯器堆疊上。  `push` 可以具有 `identifier` 和 `segment-name`。  
  
 `pop` \(選擇性\)  
 會從內部編譯器堆疊頂端移除記錄。  
  
 `identifier` \(選擇性\)  
 搭配 `push` 使用時，會指派名稱給內部編譯器堆疊的記錄。  搭配 `pop` 使用時，會將記錄推出內部堆疊，直到移除 `identifier` 為止；如果在內部堆疊找不到 `identifier`，則不會快顯任何項目。  
  
 `identifier` 可讓您使用一個 `pop` 命令即可推出多筆記錄。  
  
 "`segment-name`" \(選擇項\)  
 區段的名稱。  搭配 `pop` 使用時會推出堆疊，`segment-name` 會變成作用中區段名稱。  
  
 "`segment-class`" \(選擇項\)  
 包含這個項目可提供與 C\+\+ 2.0 以前版本的相容性。  會忽略此項。  
  
## 範例  
  
```  
// pragma_directive_const_seg.cpp  
// compile with: /EHsc  
#include <iostream>  
  
const int i = 7;               // inlined, not stored in .rdata  
const char sz1[]= "test1";     // stored in .rdata  
  
#pragma const_seg(".my_data1")  
const char sz2[]= "test2";     // stored in .my_data1  
  
#pragma const_seg(push, stack1, ".my_data2")  
const char sz3[]= "test3";     // stored in .my_data2  
  
#pragma const_seg(pop, stack1) // pop stack1 from stack  
const char sz4[]= "test4";     // stored in .my_data1  
  
int main() {  
    using namespace std;  
   // const data must be referenced to be put in .obj  
   cout << sz1 << endl;  
   cout << sz2 << endl;  
   cout << sz3 << endl;  
   cout << sz4 << endl;  
}  
```  
  
  **test1**  
**test2**  
**test3**  
**test4**   
## 註解  
 如需建立區段時不應該使用的名稱清單，請參閱 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 您也可以為初始化的資料 \([data\_seg](../preprocessor/data-seg.md)\)、未初始化的資料 \([bss\_seg](../preprocessor/bss-seg.md)\) 及函式 \([code\_seg](../preprocessor/code-seg.md)\) 指定區段。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)