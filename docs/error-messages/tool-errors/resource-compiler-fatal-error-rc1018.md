---
title: 資源編譯器嚴重錯誤 RC1018 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1018
dev_langs:
- C++
helpviewer_keywords:
- RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2c4fa0a9964c3faeed010b82f8cd98f2782fb1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028502"
---
# <a name="resource-compiler-fatal-error-rc1018"></a>資源編譯器嚴重錯誤 RC1018

未預期的 ' #elif'

`#elif`指示詞沒有出現在`#if`， **#ifdef**，或 **#ifndef**建構。

請確定沒有`#if`， **#ifdef**，或 **#ifndef**此陳述式的作用中之前的陳述式。