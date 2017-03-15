---
title: "如何：使用反映以列舉組件中的資料類型 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組件 [C++]"
  - "組件 [C++], 列舉資料類型於"
  - "資料類型 [C++], 列舉"
  - "public 成員 [C++]"
  - "public 類型 [C++]"
  - "反映 [C++], 外部組件"
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用反映以列舉組件中的資料類型 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼會示範使用 <xref:System.Reflection> 來列舉公用型別和成員。  
  
 指定組件 \(組件在本機目錄或  GAC 中\) 的名稱，則下列程式碼會嘗試開啟組件並擷取說明。  如果成功，則會顯示每個型別的公用成員。  
  
 請注意 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 要求不可使用副檔名。  因此，使用 "mscorlib.dll" 做為命令列引數會失敗，而只用 "mscorlib" 則可以顯示 .NET Framework 型別。  如果未提供組件名稱，則程式碼會偵測並回報目前組件 \(這個程式碼所產生的 EXE\) 中的型別。  
  
## 範例  
  
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
  
## 請參閱  
 [反映](../dotnet/reflection-cpp-cli.md)