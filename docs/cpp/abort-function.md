---
title: abort 函式 |Microsoft 文件
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
ms.openlocfilehash: 4acfbb5a0790dec6f7b5770832cc6b09f69a28d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="abort-function"></a>abort 函式

**中止**函式，也在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。 之間的差異**結束**和**中止**在於**結束**允許執行 c + + 執行階段終止處理 （全域物件解構函式會呼叫），而**中止**會立即終止程式。 如需詳細資訊，請參閱[中止](../c-runtime-library/reference/abort.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱

[程式終止](../cpp/program-termination.md)