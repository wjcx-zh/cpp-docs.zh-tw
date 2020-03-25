---
title: 嚴重錯誤 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202861"
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853

> '*filename*' 先行編譯標頭檔來自舊版編譯器，或先行編譯的標頭是C++ ，而且您正從 C 使用它（反之亦然）

可能的原因：

- 先行編譯標頭檔是以先前的編譯器版本編譯。 請嘗試使用目前的編譯器重新編譯標頭。

- 先行編譯的標C++頭為，而且您正從 c 使用它。請嘗試重新編譯標頭以搭配 c 使用，方法是指定其中一個[/tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將原始程式檔的尾碼變更為 "C"。 如需詳細資訊，請參閱先行[編譯器代碼的兩個選擇](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。
