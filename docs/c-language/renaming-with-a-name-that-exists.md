---
title: 以現有名稱重新命名 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: fc2a8f29-f757-4ce0-8d7f-7f8cff7f49ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b9a9c4e42356a087c8cb6c10a470ba68acd4ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067750"
---
# <a name="renaming-with-a-name-that-exists"></a>以現有名稱重新命名

**ANSI 4.9.4.2**：具有新名稱的檔案在呼叫 **rename** 函式之前即已存在時的作用

如果您嘗試使用已存在的名稱為檔案重新命名，**rename** 函式會失敗並傳回錯誤碼。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)