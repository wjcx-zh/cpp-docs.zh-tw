---
title: C + + 中的全域常數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ee5fdf3d50f30e02bd48fe3664c10d26a8449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="global-constants-in-c"></a>C++ 的全域常數
C + + 的全域常數具有靜態連結。 這是不同於 c。如果您嘗試使用的全域常數在多個檔案的 c + + 中，就會發生無法解析的外部錯誤。 編譯器最佳化全域常數，保留供變數沒有留下。  
  
 若要解決此錯誤的一個方法是包含標頭檔中的 const 初始化設定，並在必要時，就如同它是函式原型 CPP 檔案中包含該標頭。 另一個可能性是將變數設為非常數，並使用常數參考評估它。  
  
 下列範例會產生 C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 然後，  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)