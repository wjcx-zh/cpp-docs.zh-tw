---
title: 嚴重錯誤 C1382 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5a6ce312c5ef886ef25e8de46e6d3376eded2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030641"
---
# <a name="fatal-error-c1382"></a>嚴重錯誤 C1382

產生 'obj' 後已經重建 PCH 檔案 'file'。 請重建此物件

使用時[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到較 CIL.obj 指向它的.pch 檔案。 CIL.obj 檔案中的資訊已過期。 重建物件。

如果您使用編譯，也會發生 C1382 **/Yc**，但同時也傳遞多個來源的程式碼檔案給編譯器。  若要解決，請勿使用 **/Yc**時將多個來源的程式碼檔案傳遞至編譯器。  如需詳細資訊，請參閱 < [/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)。