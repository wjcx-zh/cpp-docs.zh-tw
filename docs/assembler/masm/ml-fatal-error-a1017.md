---
title: ML 嚴重錯誤 A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318055"
---
# <a name="ml-fatal-error-a1017"></a>ML 嚴重錯誤 A1017

**遺漏來原始檔案名**

ML 找不到要組合或傳遞至連結器的檔案。

當您提供 ML 命令列選項，但未指定要採取動作的檔案名時，就會產生此錯誤。 若要組合沒有 .asm 副檔名的檔案，請使用 **/Ta**命令列選項。

如果 ML 環境變數包含命令列選項，則叫用沒有參數的 ML 也可以產生此錯誤。

## <a name="see-also"></a>請參閱

[ML 錯誤訊息](ml-error-messages.md)
