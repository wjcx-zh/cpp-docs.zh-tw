---
title: 命令列錯誤 D8037 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8037
dev_langs:
- C++
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38bbb8e85f0bb11af3846435f31cfc4223a39f16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086313"
---
# <a name="command-line-error-d8037"></a>命令列錯誤 D8037

無法建立暫存 il 檔案;舊 il 檔案清除暫存目錄

沒有足夠的空間來建立暫存的編譯器中繼檔案。 若要解決這個錯誤，請移除任何舊的 MSIL 檔案中所指定的目錄**TMP**環境變數。 這些檔案都屬於表單 _CL_hhhhhhhh.ss，其中 h 代表隨機的十六進位數字，而 ss 表示 IL 檔案的類型。 此外，請務必使用最新的作業系統修補程式來更新您的電腦。

## <a name="see-also"></a>另請參閱

[命令列錯誤 D8000 至 D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)