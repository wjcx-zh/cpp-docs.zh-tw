---
title: "2.7.2.1 私用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a08faf39ab2f82d76a936c216ba6707bee5c240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="2721-private"></a>2.7.2.1 private
`private`子句宣告為私用小組的每個執行緒的變數清單中的變數。 語法`private`子句如下所示：  
  
```  
private(variable-list)  
```  
  
 在指定之變數的行為`private`子句如下所示。 具有自動儲存期的新物件配置建構。 大小和對齊新物件是由變數的類型決定。 這項配置時發生一次在小組中，每個執行緒和預設建構函式會叫用類別物件，如有必要的。否則的起始值皆不明確。  變數所參考的原始物件到建構函式進入時的不定值、 動態建構的範圍內，不得修改並具有從建構在結束時的不定值。  
  
 在指示詞的建構的語彙範圍內，變數會參照新的私用物件配置的執行緒。  
  
 若要限制`private`子句如下：  
  
-   中指定的類別類型的變數`private`子句必須具有可存取且明確預設建構函式。  
  
-   中指定的變數`private`子句不能有**const**-限定型別，除非它有類別類型與`mutable`成員。  
  
-   中指定的變數`private`子句必須沒有不完整的類型或參考類型。  
  
-   變數出現在`reduction`子句**平行**指示詞中不能指定`private`繫結至平行建構工作共用指示詞上的子句。