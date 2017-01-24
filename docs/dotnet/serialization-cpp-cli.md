---
title: "序列化 (C++/CLI) | Microsoft Docs"
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
  - ".NET Framework [C++], 序列化"
  - "Managed 程式碼 [C++], 序列化"
  - "NonSerializedAttribute 類別, Managed 應用程式"
  - "SerializableAttribute 類別, Managed 應用程式"
  - "序列化 [C++]"
  - "序列化 [C++], 關於序列化"
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 序列化 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Managed 類別 \(包括個別欄位或屬性\) 的序列化 \(Serialization，指將物件或成員的狀態儲存至永久媒體的程序\) 是由 <xref:System.SerializableAttribute> 和 <xref:System.NonSerializedAttribute> 類別所支援。  
  
## 備註  
 套用 **SerializableAttribute** 自訂屬性 \(Attribute\) 至 Managed 類別，以序列化整個類別，或只套用至特定欄位或屬性 \(Property\)，以序列化部分 Managed 類別。  使用 **NonSerializedAttribute** 自訂屬性 \(Attribute\)，以避免 Managed 類別的欄位或屬性序列化。  
  
## 範例  
  
### 說明  
 下列範例中的 `MyClass` 類別 \(以及 `m_nCount` 屬性\) 已標示為可序列化。  但是，`m_nData` 屬性 \(Property\) 是由 **NonSerialized** 自訂屬性 \(Attribute\) 所指示，因此不會序列化：  
  
### 程式碼  
  
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
  
### 註解  
 請注意，這兩個屬性 \(Attribute\) 都可用其「簡短名稱」\(**Serializable** 和 **NonSerialized**\) 參考。  這個部分將於[套用屬性](../Topic/Applying%20Attributes.md)之中作進一步說明。  
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)