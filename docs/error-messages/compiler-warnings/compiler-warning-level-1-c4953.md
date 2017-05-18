---
title: "編譯器警告 （層級 1） C4953 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: d0b8ba97d493cb6e840be1023f7c6bd29a5cbd1a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4953"></a>編譯器警告 (層級 1) C4953
已經編輯內嵌項 'function'，因為已收集分析資料，未使用分析資料  
  
 當使用[除了](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到輸入的模組之後經過重新編譯`/LTCG:PGINSTRUMENT`且出現函式 (***函式***) 的已編輯，其中，現有測試執行的候選項目為識別函式內嵌。 不過，重新編譯模組之後，函式就不再是進行內嵌的候選項目。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。
