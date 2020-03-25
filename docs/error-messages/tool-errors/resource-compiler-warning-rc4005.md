---
title: 資源編譯器警告 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182405"
---
# <a name="resource-compiler-warning-rc4005"></a>資源編譯器警告 RC4005

' identifier '：宏重新定義

此識別碼會定義兩次。 編譯器使用了第二個巨集定義。

這項警告可能是因為在命令列上，以及在程式碼中使用 `#define` 指示詞定義宏所造成。 這也可能是從 include 檔匯入宏所造成。

若要消除此警告，請移除其中一個定義，或在第二個定義之前使用 `#undef` 指示詞。
