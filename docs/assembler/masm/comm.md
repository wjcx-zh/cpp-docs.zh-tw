---
title: COMM |Microsoft 文件
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 1df6c729ab130a7ff38d7f7cf83224e7425e7dba
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="comm"></a>COMM

使用中指定的屬性建立微乎其微變數*定義*。

## <a name="syntax"></a>語法

> **COMM** *定義*[，*定義*]...

## <a name="remarks"></a>備註

共有變數配置由連結器，因此無法初始化。 這表示您不能依賴順序的這類變數的位置。

每個*定義*具有下列格式：

[*langtype*] [**NEAR** &#124; **遠**]_標籤_**:**_類型_[**:**_計數_]

選擇性*langtype*設定後面的名稱的命名慣例。 它會覆寫任何所指定的語言 **。模型**指示詞。 選擇性**NEAR**或**遠**覆寫目前的記憶體模型。 *標籤*是變數的名稱。 *類型*可以是任何類型規範 ([位元組](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)等等) 或指定的位元組數目的整數。 選擇性*計數*與宣告的資料物件中指定的元素數目預設值是其中一個。

## <a name="example"></a>範例

這個範例會建立項目的 512 位元組陣列：

```masm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)
