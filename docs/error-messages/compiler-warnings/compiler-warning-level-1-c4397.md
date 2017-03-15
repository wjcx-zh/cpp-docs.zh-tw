---
title: "編譯器警告 (層級 1) C4397 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4397"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4397"
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4397
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

DefaultCharSetAttribute 已忽略  
  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute> 是由 Visual C\+\+ 編譯器加以忽略。  若要為 DLL 指定字集，請使用 DllImport 的 CharSet 選項。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 範例  
 下列範例會產生 C4397。  
  
```  
// C4397.cpp  
// compile with: /W1 /c /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397  
  
[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK  
extern "C" bool ImportDefault(IntPtr hObject);  
  
public ref class MySettingVC {  
public:  
   void method() {  
      ImportDefault(IntPtr::Zero);  
   }  
};  
  
[StructLayout(LayoutKind::Explicit)]  
public ref struct StructDefault1{};  
  
public ref class ClassDefault1{};  
```