---
title: NMAKE 警告 U4007 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4007
dev_langs:
- C++
helpviewer_keywords:
- U4007
ms.assetid: 61ec0417-6961-43c1-ade8-f9d6e93289e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40c186e222edbb3b141fd13d8a5964e4a696edd8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087509"
---
# <a name="nmake-warning-u4007"></a>NMAKE 警告 U4007

檔名 'filename' 太長;截斷為 dos 8.3 格式

指定檔案的基底名稱超過八個字元，或延伸模組有三個以上的字元。 NMAKE 截斷了八個字元的基底和三個字元的延伸模組的名稱。

如果您的檔案系統所支援的長檔名，將名稱括雙引號括住 (**"**)。