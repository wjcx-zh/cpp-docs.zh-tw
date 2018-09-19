---
title: 資源編譯器警告 RC4005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028515"
---
# <a name="resource-compiler-warning-rc4005"></a>資源編譯器警告 RC4005

'identifier': 巨集重複定義

識別項定義了兩次。 編譯器會使用第二個巨集定義。

這個警告可能因命令列上，以及程式碼中定義的巨集`#define`指示詞。 它也可能被因從 include 檔匯入的巨集。

若要排除警告，請移除其中一個定義，或使用`#undef`指示詞，第二個定義之前。