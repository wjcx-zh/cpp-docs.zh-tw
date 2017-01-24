---
title: "bss_seg | Microsoft Docs"
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
  - "vc-pragma.bss_seg"
  - "bss_seg_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "bss_seg pragma"
  - "Pragma, bss_seg"
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bss_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定儲存在 .obj 檔案中未初始化之變數的區段。  
  
## 語法  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 備註  
 Obj 檔案可以使用 [dumpbin](../build/reference/dumpbin-command-line.md) 應用程式檢視。  .obj 檔案中未初始化之資料的預設區段是 .bss。  在某些情況下，使用 **bss\_seg** 可以透過將未初始化的資料分類至某一個區段，以加速載入時間。  
  
 未包含參數的 **bss\_seg** 會將區段重設為 .bss。  
  
 **push**\(選擇性\)  
 將記錄放置到內部編譯器堆疊上。  **push** 可以擁有 *identifier* 和 *segment\-name*。  
  
 **pop** \(選擇性\)  
 會從內部編譯器堆疊頂端移除記錄。  
  
 *identifier* \(選擇性\)  
 搭配 **push** 使用時，會指派名稱給內部編譯器堆疊的記錄。  搭配 **pop** 使用時，會從內部堆疊推出記錄，直到移除 *identifier* 為止。如果內部堆疊上找不到 *identifier*，則不會推出任何項目。  
  
 *identifier* 可透過單一 **pop** 命令推出多筆記錄。  
  
 *"segment\-name"* \(選擇性\)  
 區段的名稱。搭配 **pop** 使用時，會推出堆疊，而 *segment\-name*  會變成作用中區段名稱。  
  
 *"segment\-class"* \(選擇性\)  
 包含這個項目可提供與 C\+\+ 2.0 以前版本的相容性。  會忽略此項。  
  
## 範例  
  
```  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 您也可以為已初始化的資料 \([data\_seg](../preprocessor/data-seg.md)\), functions \([code\_seg](../preprocessor/code-seg.md)\) 和 const 變數 \([const\_seg](../preprocessor/const-seg.md)\) 指定區段。  
  
 使用 **bss\_seg** pragma 配置的資料不會保留與其位置相關的任何資訊。  
  
 如需建立區段時不應該使用的名稱清單，請參閱 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)