---
title: "ATL Archetypes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "archetype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, archetypes"
ms.assetid: 809fb0af-c0f4-4cc0-b5bc-afe3de5d9722
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ATL Archetypes
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此內容中， *原型* 是提供方法、資料成員、靜態函式、typedef，或其他功能集合的理想類別。  這個原型也包含必要的語意的說明建立或使用類別來表示特定概念。  藉由提供相同功能模擬這個原型的類別來達到相同的概念，也可以用這個原型都可以使用。  
  
 原型是用於描述的有效值功能 C\+\+ 樣板參數的。  範本的設計工具以樣板參數的必要和足夠的功能的一套清楚了解，，而且編譯器會強制使用語法必須在建置階段，不過，樣板的使用者需要文件說明語意和允許非常清楚說明的原型和類別之間的關聯性。  
  
 原型的範例在 Standard C\+\+ 程式庫是 Iterator 和容器的 Variant 型別。  這些原型。 [Iterator 慣例](../../standard-library/iterators.md) 和 [STL 容器。](../../standard-library/stl-containers.md)主題中說明。  
  
 ATL Server 定義下列原型 \(Prototype\):  
  
|名稱|描述|  
|--------|--------|  
|[背景工作原型](../../atl/reference/worker-archetype.md)|符合 *背景工作* 原型的類別提供程式碼寫入佇列管理工作項目在執行緒集區。|  
  
## 請參閱  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)