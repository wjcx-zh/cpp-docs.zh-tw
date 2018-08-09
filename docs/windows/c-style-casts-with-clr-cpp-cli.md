---
title: 使用-clr 的 C-style 轉換 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f22ca2b111cd8e408047bc051f16b6f01694b71e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641485"
---
# <a name="c-style-casts-with-clr-ccli"></a>使用 /clr 進行 C-Style 轉換 (C++/CLI)
下列主題只適用於 Common Language Runtime。  
  
 CLR 型別搭配使用時，編譯器會嘗試對應 c-style 轉換 （cast），以下列順序的下面列出的其中一個轉換：  
  
1.  const_cast  
  
2.  safe_cast  
  
3.  safe_cast plus const_cast  
  
4.  static_cast  
  
5.  static_cast plus const_cast  
  
 如果無上面所列的轉換是有效的而且運算式的類型和目標類型是 CLR 參考型別，c-style 轉換會對應至執行階段檢查 （castclass MSIL 指令）。 否則，c-style 轉換會被視為無效，則編譯器會發出錯誤。  
  
## <a name="remarks"></a>備註  
 不建議在 c-style 轉換。 進行編譯時[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)，使用[safe_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 下列範例會示範 c-style 轉換對應至**const_cast**。  
  
```cpp  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 下列範例會示範 c-style 轉換對應至**safe_cast**。  
  
```cpp  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 下列範例會示範 c-style 轉換對應至**safe_cast**加上**const_cast**。  
  
```cpp  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 下列範例會示範 c-style 轉換對應至**static_cast**。  
  
```cpp  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 下列範例會示範 c-style 轉換對應至**static_cast**加上**const_cast**。  
  
```cpp  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 下列範例會示範 c-style 轉換對應至執行階段檢查。  
  
```cpp  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 下列範例顯示無效 C 樣式轉型，導致編譯器發出錯誤。  
  
```cpp  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>需求  
 編譯器選項：`/clr`  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)