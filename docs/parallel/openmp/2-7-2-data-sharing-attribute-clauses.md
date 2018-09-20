---
title: 2.7.2 資料共用屬性子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b8c53cace8d50f10fe638ea8604c46e457f69ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392507"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 資料共用屬性子句

幾個指示詞會接受可讓使用者控制變數的共用屬性區域的持續時間的子句。 共用屬性子句僅適用於中子句出現的指示詞的語彙範圍的變數。 並非所有的下列子句允許所有指示詞。 適用於特定的指示詞的子句的清單將描述使用指示詞。

如果是變數，才會顯示平行或遇到工作共用建構，以及未共用屬性子句中指定變數或**threadprivate**指示詞，然後將變數共用。 在平行區域的動態範圍內宣告的靜態變數會在共用中。 堆積配置的記憶體 (例如，使用**malloc** C 或 c + + 或**新**運算子在 c + +) 共用。 （指標給這個記憶體，不過，可以是私人或共用）。在平行區域的動態範圍內宣告的自動儲存期的變數都是私用。

大部分的子句接受*變數清單*引數是以逗號分隔的清單會顯示的變數。 如果變數參考的資料共用屬性子句具有型別衍生自範本，而且不有任何其他程式中的該變數的參考，行為是未定義。

出現在指示詞子句後面的所有變數都必須都是可見的。 子句可能會重複，如有需要但可能在多個子句中，指定任何變數，不同之處在於變數可以指定在這兩**firstprivate**並**lastprivate**子句。

下列各節描述的資料共用屬性子句：

- **私用**，[一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 25 頁上。

- **firstprivate**，[一節 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)在 26 頁面上。

- **lastprivate**，[一節 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 27 頁面上。

- **共用**，[一節 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) 27 頁面上。

- **預設值**，[一節 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md)第 28 頁上。

- **縮減**，[一節 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md)第 28 頁上。

- **copyin**，[一節 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md)第 31 頁上。

- **copyprivate**，[一節 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) 32 頁面上。