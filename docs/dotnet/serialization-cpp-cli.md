---
title: 序列化 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988403"
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)

<xref:System.SerializableAttribute> 和 <xref:System.NonSerializedAttribute> 類別支援序列化（將物件或成員的狀態儲存到永久性媒體的處理常式）（包括個別欄位或屬性）。

## <a name="remarks"></a>備註

將**SerializableAttribute**自訂屬性套用至 managed 類別，以序列化整個類別，或只套用至特定欄位或屬性，以序列化 managed 類別的各個部分。 使用**NonSerializedAttribute**自訂屬性來豁免 managed 類別的欄位或屬性，使其無法序列化。

## <a name="example"></a>範例

### <a name="description"></a>描述

在下列範例中，類別 `MyClass` （和屬性 `m_nCount`）標示為可序列化。 不過，`m_nData` 屬性不會如非**序列化自訂**屬性所指示進行序列化：

### <a name="code"></a>程式碼

```cpp
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>註解

請注意，這兩個屬性都可以使用其「簡短名稱」（**可**序列化和非**序列化）來**參考。 這會在套用[屬性](/dotnet/standard/attributes/applying-attributes)中進一步說明。

## <a name="see-also"></a>請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
