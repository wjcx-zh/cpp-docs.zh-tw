---
title: ML 嚴重錯誤 A1017 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688555"
---
# <a name="ml-fatal-error-a1017"></a>ML 嚴重錯誤 A1017

**遺漏的來源檔案名稱**

ML 找不到組合，或將傳遞至連結器檔案。

當您讓 ML 命令列選項，而不指定要採取的檔案名稱時，會產生這個錯誤。 若要組合不.asm 副檔名的檔案、 使用 **/Ta**命令列選項。

這項錯誤也可能產生不含任何參數叫用 ML，如果 ML 環境變數包含命令列選項。

## <a name="see-also"></a>另請參閱

[ML 錯誤訊息](../../assembler/masm/ml-error-messages.md)<br/>