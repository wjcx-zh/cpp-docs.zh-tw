---
title: 2.7 資料環境 |Microsoft Docs
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
ms.openlocfilehash: 17c60c621defa15c034f57d0af8f14637db54f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378133"
---
# <a name="27-data-environment"></a>2.7 資料環境

此章節提供的指示詞和數個子句，如下所示的平行區域，在執行期間控制資料環境：

- A **threadprivate**指示詞 （請參閱下一節） 可讓執行緒本機檔案範圍、 命名空間範圍或靜態的區塊範圍變數。

- 您可以在要平行或工作共用建構期間控制變數的共用屬性的指示詞指定的子句中所述[一節 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 25 頁上。