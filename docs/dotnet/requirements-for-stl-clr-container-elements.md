---
title: "STL/CLR 容器項目的需求 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, STL"
  - "容器, STL/CLR"
  - "Standard C++ 程式庫, 樣板類別容器"
  - "STL/CLR, 容器"
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# STL/CLR 容器項目的需求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

插入 STL\/CLR 容器的所有參考型別必須最少有下列項目：  
  
-   公用的複製建構函式。  
  
-   公用的指派運算子。  
  
-   公用的解構函式。  
  
 此外，關聯的容器 \(例如 [集合](../dotnet/set-stl-clr.md) 和 [地圖](../dotnet/map-stl-clr.md) 必須有公用的比較運算子定義，預設為 `operator<` 。  容器的某些作業可能也需要公用預設建構函式和公用等價運算子定義。  
  
 如參考型別，實值型別及處理對要插入一個關聯的容器的參考型別必須有比較運算子 \(例如 `operator<` 定義。  公用複製建構函式、公開指派運算子和公用解構函式的需求為實值型別或控制代碼不存在參考型別。  
  
## 請參閱  
 [標準樣板程式庫](../misc/standard-template-library.md)