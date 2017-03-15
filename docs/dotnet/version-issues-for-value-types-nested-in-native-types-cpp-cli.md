---
title: "在原生類型中巢狀化之實值類型的版本問題 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "__nogc 類型宣告"
  - "__value 關鍵字, 使用巢狀結構時的問題"
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在原生類型中巢狀化之實值類型的版本問題 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

假設有一個用來建置 \(Build\) 用戶端組件的已簽署 \(強式名稱\) 組件元件。  此元件包含了實值型別 \(Value Type\)，在用戶端可當做原生等位成員、類別或陣列的型別。  如果此元件的未來版本變更了該實值型別的大小或配置，就必須重新編譯用戶端。  
  
 使用 [sn.exe](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) 建立金鑰檔 \(`sn -k mykey.snk`\)。  
  
## 範例  
 下列是元件的範例：  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## 範例  
 下列是用戶端的範例：  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## Output  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### 註解  
 但是，如果您在 nested\_value\_types.cpp 中為 `struct S` 加入另一個成員 \(例如 `double d;`\)，而且只重新編譯元件，未重新編譯用戶端，則結果將會產生型別為 <xref:System.IO.FileLoadException?displayProperty=fullName>\) 之未處理的例外狀況。  
  
## 請參閱  
 [Managed 類型](../dotnet/managed-types-cpp-cli.md)