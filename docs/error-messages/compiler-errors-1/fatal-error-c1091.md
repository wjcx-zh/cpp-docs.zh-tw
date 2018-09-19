---
title: 嚴重錯誤 C1091 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e93c2e6c26f8704e700465fb706867129847a460
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104233"
---
# <a name="fatal-error-c1091"></a>嚴重錯誤 C1091

編譯器限制：字串長度超過 'length' 個位元組的上限

字串常數超過目前的字串長度限制。

您可能想要將靜態字串分割成兩個 (含) 以上的變數，並使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 將結果聯結作為宣告的一部分或在執行階段時聯結。