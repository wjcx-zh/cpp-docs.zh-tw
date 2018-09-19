---
title: 運算式評估工具錯誤 CXX0065 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024160"
---
# <a name="expression-evaluator-error-cxx0065"></a>運算式評估工具錯誤 CXX0065

變數必須有堆疊框架

運算式包含變數存在於目前的範圍內，但尚未尚未建立。

當您已逐步函式，但尚未設定的函式之堆疊框架的初構，或如果您已逐步函式的結束代碼，就會發生此錯誤。

之前已設定的堆疊框架評估運算式之前，請逐步初構程式碼。

此錯誤是與 can0065 相同。