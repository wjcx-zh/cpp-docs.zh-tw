---
title: 2.7.2.3 lastprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25edca8391eb094691ef4fea3c360d351f979b43
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385959"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`子句提供的所提供的功能超集`private`子句。 語法`lastprivate`子句如下所示：

```
lastprivate(variable-list)
```

中指定的變數*變數清單*有`private`子句的語意。 當`lastprivate`識別的工作共用的建構，而每個值在指示詞上出現子句`lastprivate`循序最後一個反覆項目相關聯的迴圈中，或最後一個語彙區段指示詞中，從變數指派給變數的原始物件。 無法變數指派值的最後一個反覆項目**針對**或**的平行**，或語彙最後一節**各節**或**平行處理區段**指示詞後建構, 具有下列不定值。 未指派的子物件也會建構後有不定值。

若要限制`lastprivate`子句如下所示：

- 所有的限制，如`private`套用。

- 指定為類別類型的變數`lastprivate`必須可存取且明確的複製指派運算子。

- 在平行區域內的私用，或出現在中的變數`reduction`子句**平行**指示詞中不能指定`lastprivate`繫結至平行建構之工作共用指示詞子句。