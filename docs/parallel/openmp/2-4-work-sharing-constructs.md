---
title: 2.4 工作共用建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719b33698b708761f0cd56e65a70a6ea8fa3b053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411114"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共用的建構

工作共用建構會將執行相關聯的陳述式，會遇到相同的小組成員之間。 工作共用指示詞不會啟動新的執行緒，並在工作共用建構的項目上沒有任何隱含的障礙。

將一連串工作共用建構並**屏障**遇到的指示詞必須是相同的小組中的每個執行緒。

OpenMP 定義下列的工作共用建構，並說明下列各節：

- **針對**指示詞

- **區段**指示詞

- **單一**指示詞