---
title: 編譯器警告 （層級 1） C4397 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4397
dev_langs:
- C++
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce5c1a23c37ed572a716bdf6aa7a3216d8bdb771
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278056"
---
# <a name="compiler-warning-level-1-c4397"></a>編譯器警告 (層級 1) C4397
會忽略 DefaultCharSetAttribute  
  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute> Visual c + + 編譯器會忽略。 若要指定 DLL 的字元集，請使用 DllImport CharSet 選項。 如需詳細資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## <a name="example"></a>範例  
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