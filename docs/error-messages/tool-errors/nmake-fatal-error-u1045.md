---
title: NMAKE 嚴重錯誤 U1045 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2b9be4f7440d9e79d603e917c1886aebe7c44af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056881"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 嚴重錯誤 U1045

繁衍失敗：訊息

NMAKE 所呼叫的程式或命令因指定原因而失敗。 當 NMAKE 呼叫另一個程式 (例如，編譯器或連結器) 時，呼叫可能會失敗，或是被呼叫的程式可能會傳回錯誤。 此訊息用來報告錯誤。

如果要修正這個問題，請先判斷錯誤的原因。 您可以使用 NMAKE 所報告的命令[/N](../../build/nmake-options.md)  選項，來確認環境設定，並重複執行 NMAKE 所執行命令列上的動作。