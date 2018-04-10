---
title: 序列化 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6efd56655cb5b262eab7d7f14c197e11466fb8bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="serialization-ccli"></a>序列化 (C++/CLI)
序列化 （儲存狀態的物件或成員到永久性媒體的程序） 的 managed 類別 （包括個別欄位或屬性） 會受到<xref:System.SerializableAttribute>和<xref:System.NonSerializedAttribute>類別。  
  
## <a name="remarks"></a>備註  
 套用**SerializableAttribute**序列化整個類別或套用到特定欄位或屬性，以序列化組件的 managed 類別的 managed 類別的自訂屬性。 使用**NonSerializedAttribute**豁免的欄位或 managed 類別的屬性從序列化的自訂屬性。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，類別`MyClass`(和屬性`m_nCount`) 標示為可序列化。 不過，`m_nData`屬性則不會由序列化**因此**自訂屬性：  
  
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
 請注意，可以使用其 [簡短名稱] 參考這兩個屬性 (**Serializable**和**因此**)。 這會進一步說明[套用屬性](/dotnet/standard/attributes/applying-attributes)。  
  
## <a name="see-also"></a>請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)