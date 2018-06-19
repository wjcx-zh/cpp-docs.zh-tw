---
title: bss_seg |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b82027066e66cc51be8982a19ab6209ff236ef2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849804"
---
# <a name="bssseg"></a>bss_seg
指定儲存在 .obj 檔案中未初始化之變數的區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>備註  
 Obj 檔案可以使用檢視[dumpbin](../build/reference/dumpbin-command-line.md)應用程式。 .obj 檔案中未初始化之資料的預設區段是 .bss。 在某些情況下使用**bss_seg**可加速載入時間分組到某一區段未初始化的資料。  
  
 **bss_seg**不含任何參數區段重設為.bss。  
  
 **推入**（選擇性）  
 將記錄放置到內部編譯器堆疊上。 A**發送**可以有*識別碼*和*區段名稱*。  
  
 **pop** （選擇性）  
 會從內部編譯器堆疊頂端移除記錄。  
  
 *識別項*（選擇性）  
 當搭配**發送**，會指派名稱給內部編譯器堆疊的記錄。 搭配使用時**pop**，會將記錄在內部堆疊，直到*識別碼*已移除; 如果*識別碼*找不到在內部堆疊，不會推出。  
  
 *識別項*可讓多筆記錄即可推出以單一**pop**命令。  
  
 *「 區段名稱 」*（選擇性）  
 區段的名稱。 當搭配**pop**，時會推出堆疊和*區段名稱*會成為作用中區段名稱。  
  
 *「 區段類別 」* （選擇性）  
 包含這個項目可提供與 C++ 2.0 以前版本的相容性。 會忽略此項。  
  
## <a name="example"></a>範例  
  
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
  
 您也可以指定為初始化的資料區段 ([data_seg](../preprocessor/data-seg.md))，函式 ([code_seg](../preprocessor/code-seg.md))，和 const 變數 ([const_seg](../preprocessor/const-seg.md))。  
  
 使用配置的資料**bss_seg** pragma 不會保留與其位置相關的任何資訊。  
  
 請參閱[/section](../build/reference/section-specify-section-attributes.md)如需建立區段時，不應該使用的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)