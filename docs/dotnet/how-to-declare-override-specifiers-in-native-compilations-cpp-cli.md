---
title: "如何： 宣告覆寫規範 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f50e500cf25a18e86e107e22d58e6446d03379d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)
[密封](../windows/sealed-cpp-component-extensions.md)，[抽象](../windows/abstract-cpp-component-extensions.md)，和[覆寫](../windows/override-cpp-component-extensions.md)可用在不使用編譯中**/ZW**或[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
> [!NOTE]
>  ISO C + + 11 標準語言有[覆寫](../cpp/override-specifier.md)識別碼和[最終](../cpp/final-specifier.md)識別項，以及同時支援在 Visual Studio 使用`final`而不是`sealed`旨在的程式碼中編譯為僅限原生。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會顯示`sealed`在原生編譯中有效。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下一個範例顯示`override`在原生編譯中有效。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 這個範例將示範`abstract`在原生編譯中有效。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)