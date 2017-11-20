---
title: "如何： 包裝原生類別以便讓 C# 使用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- native code [C++], Visual C# and
- classes [C++], Visual C# and
ms.assetid: 988819ae-cc6a-4453-8ff5-be369210d962
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ff0c2a3700c20c78d3cbbf9b67810a65bb89fc3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-wrap-native-class-for-use-by-c"></a>如何：包裝原生類別以便讓 C# 使用
這個範例示範如何在包裝原生 c + + 類別，讓它可供以 C# 或其他.NET 語言撰寫的程式碼。  
  
## <a name="example"></a>範例  
  
```  
// wrap_native_class_for_mgd_consumption.cpp  
// compile with: /clr /LD  
#include <windows.h>  
#include <vcclr.h>  
#using <System.dll>  
  
using namespace System;  
  
class UnmanagedClass {  
public:  
   LPCWSTR GetPropertyA() { return 0; }  
   void MethodB( LPCWSTR ) {}  
};  
  
public ref class ManagedClass {  
public:  
   // Allocate the native object on the C++ Heap via a constructor  
   ManagedClass() : m_Impl( new UnmanagedClass ) {}  
  
   // Deallocate the native object on a destructor  
   ~ManagedClass() {  
      delete m_Impl;  
   }  
  
protected:  
   // Deallocate the native object on the finalizer just in case no destructor is called  
   !ManagedClass() {  
      delete m_Impl;  
   }  
  
public:  
   property String ^  get_PropertyA {  
      String ^ get() {  
         return gcnew String( m_Impl->GetPropertyA());  
      }  
   }  
  
   void MethodB( String ^ theString ) {  
      pin_ptr<const WCHAR> str = PtrToStringChars(theString);  
      m_Impl->MethodB(str);  
   }  
  
private:  
   UnmanagedClass * m_Impl;  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)