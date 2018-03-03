---
title: "如何： 使用 clr 編譯的原生類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c0a73d5bd9c165645dbf3c3cdee7a740cc3c16a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>如何：在 /clr 編譯中使用原生類型
您可以定義中的原生類型**/clr**編譯和使用組件中的原生類型的任何無效。 不過，原生類型不會從參考的中繼資料的使用。  
  
 每個組件必須包含它會使用每個原生類型的定義。  
  
 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 這個範例會建立定義及使用原生類型的元件。  
  
```  
// use_native_type_in_clr.cpp  
// compile with: /clr /LD  
public struct NativeClass {  
   static int Test() { return 98; }  
};  
  
public ref struct ManagedClass {  
   static int i = NativeClass::Test();  
   void Test() {  
      System::Console::WriteLine(i);  
   }  
};  
```  
  
## <a name="example"></a>範例  
 這個範例會定義的用戶端所使用的元件。 請注意，它會存取原生類型中，發生錯誤，除非它在編譯模組中定義。  
  
```  
// use_native_type_in_clr_2.cpp  
// compile with: /clr  
#using "use_native_type_in_clr.dll"  
// Uncomment the following 3 lines to resolve.  
// public struct NativeClass {  
//    static int Test() { return 98; }  
// };  
  
int main() {  
   ManagedClass x;  
   x.Test();  
  
   System::Console::WriteLine(NativeClass::Test());   // C2653  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)