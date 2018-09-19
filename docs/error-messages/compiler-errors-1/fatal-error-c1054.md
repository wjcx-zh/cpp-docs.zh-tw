---
title: 嚴重錯誤 C1054 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439019b1f510127ae54e77d445d59e86be09a49b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101965"
---
# <a name="fatal-error-c1054"></a>嚴重錯誤 C1054

編譯器限制： 初始設定式巢狀太深

程式碼超過初始設定式 （10 至 15 層級，根據正在初始化的類型的組合） 的巢狀限制。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 簡化的資料類型，以減少巢狀結構正在初始化。

1. 初始化個別的陳述式中的變數宣告之後。