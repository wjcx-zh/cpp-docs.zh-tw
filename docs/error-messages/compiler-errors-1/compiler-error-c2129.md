---
title: 編譯器錯誤 C2129 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e86515a7d7c8954271578291c4ebcb1a52fc9863
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054281"
---
# <a name="compiler-error-c2129"></a>編譯器錯誤 C2129

靜態函式 'function' 宣告但未定義

向前參考對`static`永遠不會定義函式。

A`static`函式必須在檔案範圍內定義。 如果函式定義於另一個檔案，它必須宣告`extern`。