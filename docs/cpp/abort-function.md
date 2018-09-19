---
title: abort 函式 |Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6e0b7dc49fbc53eb5e079657d98380d10bedf4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036484"
---
# <a name="abort-function"></a>abort 函式

**中止**函式，也在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。 之間的差異`exit`並**中止**在於`exit`可讓 c + + 執行階段終止處理 （全域物件會呼叫解構函式），而**中止**立即終止程式。 如需詳細資訊，請參閱 <<c0> [ 中止](../c-runtime-library/reference/abort.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱

[程式終止](../cpp/program-termination.md)