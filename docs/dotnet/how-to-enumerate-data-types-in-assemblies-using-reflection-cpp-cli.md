---
title: "如何： 列舉資料型別使用反映 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 209124e6d4e8afa7930a4c74d2cce1acd7e279b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enumerate-data-types-in-assemblies-using-reflection-ccli"></a>如何：使用反映以列舉組件中的資料類型 (C++/CLI)
下列程式碼示範的公用類型和成員使用列舉<xref:System.Reflection>。  
  
 指定組件的名稱之後的本機目錄中或是 GAC 中，下列程式碼會嘗試開啟組件，並擷取說明。 如果成功的話，每個型別會顯示其公用成員。  
  
 請注意，<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>要求使用沒有副檔名。 因此，使用"mscorlib.dll"做為命令列引數將會失敗，使用時只是"mscorlib"將會造成.NET Framework 型别的顯示。 如果不提供任何組件名稱，程式碼會偵測並回報目前的組件中的型別 (這段程式碼所產生的 EXE)。  
  
## <a name="example"></a>範例  
  
```  
// self_reflection.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
using namespace System::Collections;  
  
public ref class ExampleType {  
public:  
   ExampleType() {}  
   void Func() {}  
};  
  
int main() {  
   String^ delimStr = " ";  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ args = Environment::CommandLine->Split( delimiter );  
  
// replace "self_reflection.exe" with an assembly from either the local  
// directory or the GAC  
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");  
   Console::WriteLine(a);  
  
   int count = 0;  
   array<Type^>^ types = a->GetTypes();  
   IEnumerator^ typeIter = types->GetEnumerator();  
  
   while ( typeIter->MoveNext() ) {  
      Type^ t = dynamic_cast<Type^>(typeIter->Current);  
      Console::WriteLine("   {0}", t->ToString());  
  
      array<MemberInfo^>^ members = t->GetMembers();  
      IEnumerator^ memberIter = members->GetEnumerator();  
      while ( memberIter->MoveNext() ) {  
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);  
         Console::Write("      {0}", mi->ToString( ) );  
         if (mi->MemberType == MemberTypes::Constructor)  
            Console::Write("   (constructor)");  
  
         Console::WriteLine();  
      }  
      count++;  
   }  
   Console::WriteLine("{0} types found", count);  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [反映 (C++/CLI)](../dotnet/reflection-cpp-cli.md)