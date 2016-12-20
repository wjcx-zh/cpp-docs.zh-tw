---
title: "C-Style Casts with /clr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C-style casts and /clr"
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C-Style Casts with /clr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列主題只適用於 Common Language Runtime。  
  
 當使用 CLR 型別，編譯器會嘗試將 C\-Style 轉換到會依照下列順序下面所列的，其中一個轉換:  
  
1.  const\_cast  
  
2.  safe\_cast  
  
3.  safe\_cast 加上 const\_cast  
  
4.  static\_cast  
  
5.  static\_cast 加上 const\_cast  
  
 如果轉換都沒有清單頂端，有效，而且，如果運算式的型別和目標型別是 CLR 參考型別， C\-Style 轉換對應至執行階段檢查 \(castclass MSIL 指令\)。  否則， C 樣式轉換視為無效，所以編譯器會發出錯誤。  
  
## 備註  
 不建議使用 C 樣式轉換。  使用 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)編譯時，請使用 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 下列範例顯示 C 樣式轉換其對應至 `const_cast`。  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 下列範例顯示 C 樣式轉換其對應至 `safe_cast`。  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 下列範例顯示 C 樣式轉換其對應至 `safe_cast` 加上 `const_cast`。  
  
```  
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
  
 下列範例顯示 C 樣式轉換其對應至 `static_cast`。  
  
```  
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
  
 下列範例顯示 C 樣式轉換其對應至 `static_cast` 加上 `const_cast`。  
  
```  
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
  
 下列範例顯示 C 樣式轉換其對應至執行階段檢查。  
  
```  
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
  
 下列範例顯示無效的 C 樣式轉換，使編譯器發出錯誤。  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## 需求  
 編譯器選項：**\/clr**  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)