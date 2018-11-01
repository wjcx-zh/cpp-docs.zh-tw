---
title: 資源編譯器警告 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613599"
---
# <a name="resource-compiler-warning-rc4005"></a>資源編譯器警告 RC4005

'identifier': 巨集重複定義

識別項定義了兩次。 編譯器會使用第二個巨集定義。

這個警告可能因命令列上，以及程式碼中定義的巨集`#define`指示詞。 它也可能被因從 include 檔匯入的巨集。

若要排除警告，請移除其中一個定義，或使用`#undef`指示詞，第二個定義之前。