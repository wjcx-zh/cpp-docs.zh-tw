---
title: 嚴重錯誤 C1046 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1046
dev_langs:
- C++
helpviewer_keywords:
- C1046
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 449b181167ef493c149e9e34cb2f1a681148411d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035460"
---
# <a name="fatal-error-c1046"></a>嚴重錯誤 C1046

編譯器限制： 結構巢狀太深

結構、 等位或類別超過巢狀限制，也就是 15 層級。 請重寫的定義，以減少巢狀層級。 結構、 等位或類別使用分割成兩個或多個部分`typedef`來定義一或多個巢狀結構。