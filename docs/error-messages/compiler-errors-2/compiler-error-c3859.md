---
title: 編譯器錯誤 C3859 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06a09a6ad66384fd2b5423e3df046771f7653
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053385"
---
# <a name="compiler-error-c3859"></a>編譯器錯誤 C3859

超出 PCH 的虛擬記憶體範圍；請使用等於或大於 '-Zmvalue' 的命令列選項重新編譯

先行編譯標頭檔對編譯器正在嘗試放入其中的資料量而言太小。 使用 **/Zm**編譯器旗標，指定較大的值，為先行編譯標頭檔。 如需詳細資訊，請參閱 < [/Zm （指定先行編譯標頭記憶體配置上限）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。