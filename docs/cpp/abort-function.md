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
ms.openlocfilehash: 3e5679ce718c564ee40fb07b676756ef79344a99
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403618"
---
# <a name="abort-function"></a>abort 函式

**中止**函式，也在標準 include 檔中宣告\<stdlib.h >，會終止 c + + 程式。 之間的差異`exit`並**中止**在於`exit`可讓 c + + 執行階段終止處理 （全域物件會呼叫解構函式），而**中止**立即終止程式。 如需詳細資訊，請參閱 <<c0> [ 中止](../c-runtime-library/reference/abort.md)中*執行階段程式庫參考*。

## <a name="see-also"></a>另請參閱
[程式終止](../cpp/program-termination.md)