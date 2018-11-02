---
title: 資源編譯器錯誤 RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: deabd639e04d5b78b398cda9245e9726e2124740
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642919"
---
# <a name="resource-compiler-error-rc2144"></a>資源編譯器錯誤 RC2144

PRIMARY LANGUAGE ID 不是數字

PRIMARY LANGUAGE ID 必須是十六進位語言 ID。 請參閱《執行階段程式庫參考》 [](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) 中的 *語言和國家/地區字串* ，以取得有效語言 ID 的清單。

如果已在 .RC 檔案中使用工具加入和刪除資源，也會發生此錯誤。 若要修正這個問題，請在文字編輯器中開啟 .RC 檔案，並以手動方式清除任何未使用的資源。