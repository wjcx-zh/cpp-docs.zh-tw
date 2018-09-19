---
title: 嚴重錯誤 C1854 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83450169ec928bb77e46916619c84b3b9a3443a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029386"
---
# <a name="fatal-error-c1854"></a>嚴重錯誤 C1854

> 無法覆寫在目的檔中先行編譯標頭的建立期間形成的資訊: '*filename*'

您指定[/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)選項指定之後[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)在同一個檔案的選項。

若要修正此問題，在一般情況下，只有一個檔案中設定您的專案編譯所 **/Yc**選項，並設定要編譯使用的所有其他檔案 **/Yu**選項。 如需有關使用 **/Yc**選項，以及如何在 Visual Studio IDE 中設定，請參閱[/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。 如需有關使用先行編譯標頭的詳細資訊，請參閱 <<c0> [ 建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)。
