---
title: "嚴重錯誤 C1307 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1173f538f02e8178d523bb51476b4a10427099ea
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1307"></a>嚴重錯誤 C1307
在收集分析資料時已對程式進行編輯  
  
 當使用[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 連結器偵測到重新編譯之後 /ltcg: pginstrument 的輸入的模組和模組已變更為現有的設定檔資料所在不再相關的點。 例如，如果重新編譯的模組中，變更的呼叫歷程圖，編譯器會產生 C1307。  
  
 若要解決這個錯誤，執行 /ltcg: pginstrument、 取消復原所有測試回合，並執行 /ltcg: pgoptimize。 如果您無法執行 /ltcg: pginstrument 和取消復原所有測試回合，改用除了 /ltcg: pgoptimize 建立最佳化映像。
