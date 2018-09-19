---
title: 運算式評估工具錯誤 CXX0044 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0044
dev_langs:
- C++
helpviewer_keywords:
- CXX0044
- CAN0044
ms.assetid: d59868b5-c1ec-46ac-91d6-5d575a4d6b49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34adab6500683d8b78a4ce9c990eaf04c143e424
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064707"
---
# <a name="expression-evaluator-error-cxx0044"></a>運算式評估工具錯誤 CXX0044

使用 _based(void) 指標必須有 :> 運算子

指標根據`void`不能直接使用。 您必須形成完整的指標，使用 **: >** 運算子。

此錯誤是與 can0044 相同。