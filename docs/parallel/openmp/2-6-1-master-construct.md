---
title: 2.6.1 master 建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445629"
---
# <a name="261-master-construct"></a>2.6.1 master 建構

**主要**指示詞會識別指定小組的主要執行緒所執行的結構化的區塊的建構。 語法**主要**指示詞時，如下所示：

```
#pragma omp master new-linestructured-block
```

在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有任何隱含的障礙，項目，或從 master 建構結束。