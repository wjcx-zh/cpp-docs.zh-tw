---
title: ML 錯誤訊息
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 1b065433a1a6baf9bf2631aeb2f53421f8efb83b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312621"
---
# <a name="ml-error-messages"></a>ML 錯誤訊息

MASM 元件所產生的錯誤訊息可分為三個類別：

- **嚴重錯誤。** 這表示嚴重的問題，導致公用程式無法完成其正常進程。

- **非嚴重錯誤。** 公用程式可能會完成其進程。 如果有的話，其結果就不可能是您想要的。

- **消息.** 這些訊息表示可能會讓您無法取得所需結果的條件。

所有的錯誤訊息都採用下列形式：

> *公用程式*： *Filename* （*行*）： {*Error_type*} （*Code*）： *Message_text*

其中：

*公用程式*\
傳送錯誤訊息的程式。

*檔案名*\
包含錯誤產生條件的檔案。

*行*\
錯誤條件存在的近似行。

*Error_type*\
嚴重錯誤、錯誤或警告。

程式*代碼*\
唯一的5或6位數的錯誤碼。

*Message_text*\
錯誤狀況的簡短和一般描述。

## <a name="see-also"></a>另請參閱

[Microsoft 巨集組譯參考](microsoft-macro-assembler-reference.md)
