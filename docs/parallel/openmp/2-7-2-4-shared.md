---
title: 2.7.2.4 共用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1a545f1c505f9f578cad682399c8d69a882824
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400142"
---
# <a name="2724-shared"></a>2.7.2.4 shared

這個子句共用中出現的變數*變數清單*小組中的所有執行緒之間。 在小組的所有執行緒都存取相同的儲存區，如**共用**變數。

語法**共用**子句如下所示：

```
shared(variable-list)
```