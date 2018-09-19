---
title: 無連結 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acbce1b4a4a19c5fa1a015e01bd2078fc70f6e1c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063080"
---
# <a name="no-linkage"></a>無連結

如果區塊中某個識別項的宣告並未包含 `extern` 儲存類別指定名稱，則不會連結識別項，且該識別項在函式中是唯一的。

下列識別項不會進行連結：

- 除了物件或函式之外，可項識別項宣告為任何項目

- 宣告為函式參數的識別項

- 已宣告不含 `extern` 儲存類別指定名稱之物件的區塊範圍識別項

如果識別項未連結，則在相同範圍層級中再次宣告相同名稱 (在宣告子或類型指定名稱中) 會產生符號重新定義錯誤。

## <a name="see-also"></a>請參閱

[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)