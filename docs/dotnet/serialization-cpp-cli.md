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
ms.openlocfilehash: 794a71ae9a146b691ba6a4377a7fdf2c3ddd3501
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741397"
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)

序列化 （儲存狀態的物件或成員，才能永久媒體的程序） 的 managed 類別 （包括個別的欄位或屬性） 受到<xref:System.SerializableAttribute>和<xref:System.NonSerializedAttribute>類別。

## <a name="remarks"></a>備註

適用於**SerializableAttribute**至受管理的類別，以序列化整個類別，或套用到特定的欄位或屬性序列化的 managed 類別的組件的自訂屬性。 使用**NonSerializedAttribute**豁免的欄位或 managed 類別的屬性從序列化的自訂屬性。

## <a name="example"></a>範例

### <a name="description"></a>描述

在下列範例中，類別`MyClass`(和屬性`m_nCount`) 標示為可序列化。 不過，`m_nData`屬性則不會序列化所示**NonSerialized**自訂屬性：

### <a name="code"></a>程式碼

```
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

請注意，可以使用其 「 簡短名稱 」 參考這兩個屬性 (**Serializable**並**NonSerialized**)。 這會進一步說明[套用屬性](/dotnet/standard/attributes/applying-attributes)。

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
