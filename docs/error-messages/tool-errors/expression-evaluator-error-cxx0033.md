---
title: "運算式評估工具錯誤 CXX0033 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0033
dev_langs: C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49f2b6221d385587fa5e62af51d37eb7d3b78872
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0033"></a>運算式評估工具錯誤 CXX0033
OMF 類型資訊的錯誤  
  
 可執行檔的檔案沒有有效的物件模組格式 (OMF) 進行偵錯。  
  
 這個錯誤是與 can0033 相同。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  不使用釋放與此版本的 Visual c + + 連結器建立可執行檔。 重新連結使用目前的 LINK.exe 版本的物件程式碼。  
  
2.  .Exe 檔案可能已損毀。 重新編譯並重新連結程式。