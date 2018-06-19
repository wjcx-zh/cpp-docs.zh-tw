---
title: detect_mismatch |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f30afed5acdb9da433f7ce5f992df9bcb6dc8f5
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33953955"
---
# <a name="detectmismatch"></a>detect_mismatch
在物件中放入記錄。 連結器會檢查這些記錄是否有不相符之處。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>備註  
 當您連結專案時，如果專案包含兩個具有同一個 `LNK2038` 的物件，但其中一個物件的 `name` 不同，則連結器會擲回 `value` 錯誤。 使用這個 pragma 可防止連結不一致的目的檔。  
  
 名稱和數值都是字串常值，而且遵守字串常值的逸出字元與串連規則。 名稱和數值區分大小寫，而且不能包含逗號、等號、引號或 `null` 字元。  
  
## <a name="example"></a>範例  
 這個範例會建立兩個版本號碼不同但版本標籤相同的檔案。  
  
```  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
 如果您使用命令列 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 編譯這兩個檔案，將會收到 `LNK2038` 錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)