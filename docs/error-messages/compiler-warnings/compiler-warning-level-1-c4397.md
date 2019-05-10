---
title: 編譯器警告 (層級 1) C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: 7f0a3c31f460a66523ed1c327cee097dc890bbeb
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447668"
---
# <a name="compiler-warning-level-1-c4397"></a>編譯器警告 (層級 1) C4397

已忽略 DefaultCharSetAttribute

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> Microsoft 會忽略C++編譯器。 若要指定為 DLL 的字元，使用 DllImport 的 CharSet 選項。 如需詳細資訊，請參閱 <<c0> [ 使用C++Interop (隱含 PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。</c0>

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