---
title: 3.3 計時常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c9eda9ac8f60e66c8c4168d734bcf4459b0b63e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403977"
---
# <a name="33-timing-routines"></a>3.3 計時常式

在本節中所述的函式支援可攜式時鐘計時器：

- `omp_get_wtime`函式會傳回 24 小時制的時鐘時間。

- `omp_get_wtick`函式會傳回連續的時鐘刻度之間的秒數。