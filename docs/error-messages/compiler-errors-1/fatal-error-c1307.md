---
title: 嚴重錯誤 C1307 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d06ce51ada7cd9159b8e02ff627bf12ebb7293d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1307"></a>嚴重錯誤 C1307
在收集分析資料時已對程式進行編輯  
  
 當使用[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 連結器偵測到重新編譯之後 /ltcg: pginstrument 的輸入的模組和模組已變更為現有的設定檔資料所在不再相關的點。 例如，如果重新編譯的模組中，變更的呼叫歷程圖，編譯器會產生 C1307。  
  
 若要解決這個錯誤，執行 /ltcg: pginstrument、 取消復原所有測試回合，並執行 /ltcg: pgoptimize。 如果您無法執行 /ltcg: pginstrument 和取消復原所有測試回合，改用除了 /ltcg: pgoptimize 建立最佳化映像。