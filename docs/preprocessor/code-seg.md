---
title: code_seg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs:
- C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57511efccff22a1f1d6e7dcd957d75066b072c55
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="codeseg"></a>code_seg
指定文字區段，其中函式儲存在 .obj 檔案中。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>備註  
 `code_seg` pragma 指示詞不會控制針對具現化樣板所產生之目的碼及編譯器隱含產生之程式碼的位置 (例如特殊的成員函式)。 我們建議您改用[__declspec(code_seg(...))](../cpp/code-seg-declspec.md)屬性相反地，因為它可讓您控制所有目的碼的位置。 這包括編譯器產生的程式碼。  
  
 A*區段*在.obj 檔案會是資料是載入成為記憶體單位的具名的區塊。 A*文字區段*是包含可執行程式碼區段。 在本文中的條款*區段*和*區段*交換使用。  
  
 `code_seg` pragma 指示詞會通知編譯器將轉譯單位中的後續目標程式碼全數放入名為 `segment-name` 的文字區段。 根據預設，.obj 檔中函式所使用的文字區段是具名的 .text。  
  
 沒有參數的 `code_seg` pragma 指示詞會將後續目的碼的文字區段名稱變更為 .text。  
  
 **推入**（選擇性）  
 將記錄放置到內部編譯器堆疊上。 A**發送**可以有`identifier`和`segment-name`。  
  
 **pop** （選擇性）  
 會從內部編譯器堆疊頂端移除記錄。  
  
 `identifier` (選擇性)  
 當搭配**發送**，會指派名稱給內部編譯器堆疊的記錄。 當搭配**pop**，會將記錄在內部堆疊，直到`identifier`已移除; 如果`identifier`找不到在內部堆疊，不會推出。  
  
 `identifier` 可讓多筆記錄即可只使用一個推出**pop**命令。  
  
 "`segment-name`" (選擇項)  
 區段的名稱。 當搭配**pop**，時會推出堆疊和`segment-name`會變成作用中的文字區段名稱。  
  
 "`segment-class`" (選擇項)  
 會被忽略，包含的原因是為了與 2.0 版以前的 C++ 版本相容。  
  
 您可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)應用程式檢視.obj 檔。 各支援目標架構的 DUMPBIN 版本隨附於 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## <a name="example"></a>範例  
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
  
 如需不應該用來建立的區段名稱的清單，請參閱[/section](../build/reference/section-specify-section-attributes.md)。  
  
 您也可以指定為初始化的資料區段 ([data_seg](../preprocessor/data-seg.md))，未初始化的資料 ([bss_seg](../preprocessor/bss-seg.md))，和 const 變數 ([const_seg](../preprocessor/const-seg.md))。  
  
## <a name="see-also"></a>請參閱  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)