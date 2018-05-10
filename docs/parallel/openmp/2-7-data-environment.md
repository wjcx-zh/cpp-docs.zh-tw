---
title: 2.7 資料環境 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="27-data-environment"></a>2.7 資料環境
本節提供的指示詞和幾個子句，如下所示的平行區域，在執行期間控制資料環境：  
  
-   A **threadprivate**指示詞 （請參閱下一節） 可讓執行緒本機檔案範圍、 命名空間範圍或靜態的區塊範圍變數。  
  
-   您可以在平行或工作共用建構期間控制共用的變數屬性的指示詞指定的子句中所述[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)在 25 頁面上。