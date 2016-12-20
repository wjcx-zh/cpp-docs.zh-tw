---
title: "從預存程序使用多重結果集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "多個結果集"
  - "預存程序, 傳回結果集"
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從預存程序使用多重結果集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

大多數的預存程序會傳回多個結果集。  這種預存程序通常包含了一或多個 Select 陳述式。  消費者必須考慮這點來處理所有的結果集。  
  
### 若要處理多個結果集  
  
1.  使用做為樣板引數的 `CMultipleResults` 和所選擇的存取子以建立 `CCommand` 類別。  通常，這會是動態存取子或手動存取子。  如果您使用了其他存取子型別，可能就無法決定每個資料列集的輸出資料行。  
  
2.  依照一般方式執行預存程序並繫結該資料行 \(請參閱[我該如何擷取資料？](../../data/oledb/fetching-data.md)\)。  
  
3.  使用資料。  
  
4.  在 `CCommand` 類別上呼叫 `GetNextResult`。  如果有另一個結果資料列集可以使用，`GetNextResult` 會傳回 S\_OK，而如果您使用的是手動存取子，您便應該重新繫結您的資料行。  如果 `GetNextResult` 傳回一個錯誤，表示沒有其他可用的結果集。  
  
## 請參閱  
 [使用預存程序](../../data/oledb/using-stored-procedures.md)