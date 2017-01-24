---
title: "編譯器錯誤 CS0021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0021
無法套用有 \[\] 的索引至類型 'type' 的運算式  
  
 嘗試透過不支援 [索引子](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md) 的資料類型上的索引子來存取值。  
  
 嘗試在 C\+\+ 組件中使用索引子時，可能會得到 CS0021。 在此情況下，請為 C\+\+ 類別加上 `DefaultMember` 屬性，讓 C\# 編譯器知道哪一個索引子是預設值。 下列範例會產生 CS0021：  
  
## 範例  
 這個檔案會編譯成 .dll 檔案 — 並將 `DefaultMember` 屬性標記為註解，以便產生錯誤。  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## 範例  
 以下是呼叫 .dll 檔案的 C\# 檔案。 這個檔案嘗試透過索引子存取類別，但因為沒有任何成員宣告為要使用的預設索引子，所以產生錯誤。  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```