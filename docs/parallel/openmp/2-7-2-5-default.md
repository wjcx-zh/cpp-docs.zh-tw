---
title: 2.7.2.5 預設 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 047110fe80d15d0ff3d979eeec8abf3e42dc35f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401559"
---
# <a name="2725-default"></a>2.7.2.5 default

**預設**子句可讓使用者會影響變數的資料共用屬性。 語法**預設**子句如下所示：

```
default(shared | none)
```

指定**default(shared)** 相當於明確列出每個中的目前可見變數**共用**子句，除非它是**threadprivate**或**cons**`t`-限定。 沒有明確**預設**的預設行為是相同子句中，如果**default(shared)** 所指定。

指定**default （none)** 至少下列其中之一必須是針對至平行建構的語彙範圍中變數的每個參考，則為 true:

- 變數會明確地列出建構包含參考的資料共用屬性子句中。

- 在平行建構中宣告的變數。

- 變數是**threadprivate**。

- 變數具有**const**-限定型別。

- 變數是 for 迴圈控制變數**針對**緊接在後面的迴圈**如**或**平行的**指示詞，且變數參考會出現在迴圈內.

在指定的變數**firstprivate**， **lastprivate**，或**減少**括住的指示詞子句會造成該變數的隱含參考封閉式內容。 這類隱含的參考也限於上面所列的需求。

只有一個**預設**您可以在指定子句**平行**指示詞。

變數的預設資料共用屬性，可以使用覆寫**私人**， **firstprivate**， **lastprivate**，**減少**，並**共用**子句，如下列範例所示：

```
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```