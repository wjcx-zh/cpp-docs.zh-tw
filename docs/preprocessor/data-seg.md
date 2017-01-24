---
title: "data_seg | Microsoft Docs"
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
  - "data_seg_CPP"
  - "vc-pragma.data_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "data_seg pragma"
  - "Pragma, data_seg"
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# data_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定儲存在 .obj 檔案中已初始化之變數的資料區段。  
  
## 語法  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 備註  
 在本主題中，「*區段*」\(Segment\) 和「*區段*」\(Section\) 這兩個詞的意義可互換。  
  
 OBJ 檔案可以使用 [dumpbin](../build/reference/dumpbin-command-line.md) 應用程式檢視。  .obj 檔案中已初始化之變數的預設區段是 .data。  未初始化的變數會被視為要初始化為零，並儲存在 .bss 中。  
  
 未包含參數的 **data\_seg** 會將區段重設為 .data。  
  
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
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 使用 **data\_seg** 配置的資料不會保留與其位置相關的任何資訊。  
  
 如需建立區段時不應該使用的名稱清單，請參閱 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 您也可以為 const 變數 \([const\_seg](../preprocessor/const-seg.md)\)、未初始化的資料 \([bss\_seg](../preprocessor/bss-seg.md)\) 及函式 \([code\_seg](../preprocessor/code-seg.md)\) 指定區段。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)