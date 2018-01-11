---
title: "輸入資料流操作工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17242528dd2be4a72a763f34ee651fc170fea58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="input-stream-manipulators"></a>輸入資料流操作工具
許多操作工具 (例如 [setprecision]--brokenlink--(../Topic/not%20found:3ddde610-70cc-4cfa-8a89-3e83d1d356a8.md#setprecision)) 是為 `ios` 類別定義的，因此適用於輸入資料流。 不過，有少數操作工具實際上會影響到輸入資料流物件。 在這些會影響到輸入資料流物件的操作工具中，最重要的是基數操作工具 `dec`、`oct` 及 `hex`，這些會決定與來自輸入資料流的數字搭配使用的轉換底數。  
  
 進行擷取時，`hex` 操作工具可允許處理各種輸入格式。 例如 c、C、0xc、0xC、0Xc 及 0XC 全部都會解譯為十進位整數 12。 任何 0 到 9、A 到 F、a 到 f、x 和 X 以外的字元都會終止數字轉換。 因此，在已設定 [basic_ios::fail](../standard-library/basic-ios-class.md#fail) 位元的情況下，序列 `"124n5"` 會轉換成數字 124。  
  
## <a name="see-also"></a>請參閱  
 [輸入資料流](../standard-library/input-streams.md)

