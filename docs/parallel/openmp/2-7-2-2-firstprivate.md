---
title: 2.7.2.2 firstprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e6ad966f4cf895da9374798f6c9a4079ccc2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400961"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

**Firstprivate**子句提供的所提供的功能超集**私人**子句。 語法**firstprivate**子句如下所示：

```
firstprivate(variable-list)
```

中指定的變數*變數清單*有**私人**子句的語意，如中所述[一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) 25 頁上。 如同它已執行過一次每個執行緒，則建構的執行緒執行前，可發生初始化或建構。 針對**firstprivate**平行建構子句，新的私用物件的初始值是之前遇到執行緒的平行建構存在的原始物件的值。 針對**firstprivate**工作共用建構上的子句，每個執行緒執行的工作共用建構新的私用物件的初始值是時間點之前存在的原始物件的值，在相同的執行緒遇到的工作共用建構。 此外，對於 c + + 物件，每個執行緒的新私用物件是複製建構自原始物件。

若要限制**firstprivate**子句如下所示：

- 中指定的變數**firstprivate**子句不能是不完整的類型或參考型別。

- 指定為類別類型的變數**firstprivate**必須可存取且明確的複製建構函式。

- 在平行區域內的私用，或出現在中的變數**縮減**子句**平行**指示詞中不能指定**firstprivate**子句工作共用指示詞繫結至平行建構。