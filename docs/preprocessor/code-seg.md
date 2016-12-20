---
title: "code_seg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "code_seg_CPP"
  - "vc-pragma.code_seg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "code_seg pragma"
  - "Pragma, code_seg"
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# code_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定文字區段，其中函式儲存在 .obj 檔案中。  
  
## 語法  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## 備註  
 `code_seg` pragma 指示詞不會控制針對具現化樣板所產生之目的碼及編譯器隱含產生之程式碼的位置 \(例如特殊的成員函式\)。  建議您改用 [\_\_declspec\(code\_seg\(...\)\)](../cpp/code-seg-declspec.md) 屬性，因為此屬性可讓您控制所有目的碼的位置。  這包括編譯器產生的程式碼。  
  
 .obj 檔中的「*區段*」\(Segment\) 是載入成為記憶體單位的具名資料區塊。  「*文字區段*」\(Text Segment\) 是包含可執行程式碼的區段。  本文中的「*區段*」\(Segment\) 和「*區段*」\(Section\) 這兩個詞可互換。  
  
 `code_seg` pragma 指示詞會通知編譯器將轉譯單位中的後續目標程式碼全數放入名為 `segment-name` 的文字區段。  根據預設，.obj 檔中函式所使用的文字區段是具名的 .text。  
  
 沒有參數的 `code_seg` pragma 指示詞會將後續目的碼的文字區段名稱變更為 .text。  
  
 **Push** \(選擇性\)  
 將記錄放置到內部編譯器堆疊上。  **push** 可以具有 `identifier` 和 `segment-name`。  
  
 **pop** \(選擇性\)  
 會從內部編譯器堆疊頂端移除記錄。  
  
 `identifier` \(選擇性\)  
 搭配 **push** 使用時，會指派名稱給內部編譯器堆疊的記錄。  搭配 **pop** 使用時，會將記錄推出內部堆疊，直到移除 `identifier` 為止；如果在內部堆疊找不到 `identifier`，則不會快顯任何項目。  
  
 `identifier` 可讓您只使用一個 **pop** 命令即可推出多筆記錄。  
  
 "`segment-name`" \(選擇項\)  
 區段的名稱。  搭配 **pop** 使用時會推出堆疊，`segment-name` 會變成作用中文字區段名稱。  
  
 "`segment-class`" \(選擇項\)  
 會被忽略，包含的原因是為了與 2.0 版以前的 C\+\+ 版本相容。  
  
 您可以使用 [DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) 應用程式檢視 .obj 檔。  各支援目標架構的 DUMPBIN 版本隨附於 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## 範例  
 這個範例示範如何使用 `code_seg` pragma 指示詞控制目的碼的位置：  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 如需建立區段時不應該使用的名稱清單，請參閱 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 您也可以為初始化的資料 \([data\_seg](../preprocessor/data-seg.md)\)、未初始化的資料 \([bss\_seg](../preprocessor/bss-seg.md)\) 及 const 變數 \([const\_seg](../preprocessor/const-seg.md)\) 指定區段。  
  
## 請參閱  
 [code\_seg \(\_\_declspec\)](../cpp/code-seg-declspec.md)   
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)