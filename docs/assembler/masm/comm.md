---
title: 通訊 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690028"
---
# <a name="comm"></a>COMM

使用中指定的屬性建立微乎其微變數*定義*。

## <a name="syntax"></a>語法

> **COMM** *定義*[，*定義*]...

## <a name="remarks"></a>備註

微乎其微變數所配置之連結器，因此無法初始化。 這表示您不能依賴這類變數的順序的位置。

每個*定義*具有下列格式：

[*langtype*] [**NEAR** &#124; **FAR**]_標籤_**:**_類型_[**:**_計數_]

選擇性*langtype*設定後面的名稱的命名慣例。 它會覆寫所指定的任何語言 **。模型**指示詞。 選擇性**NEAR**或是**FAR**覆寫目前的記憶體模型。 *標籤*是變數的名稱。 *型別*可以是任何類型規範 ([位元組](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)等等) 或指定的位元組數目的整數。 選擇性*計數*宣告的資料物件中指定的元素數目的預設值是 1。

## <a name="example"></a>範例

這個範例會建立陣列的 512 位元組的項目：

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
