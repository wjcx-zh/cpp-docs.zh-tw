---
title: 設定登錄器程式碼的靜態連結 (僅限 C++)
description: 如何以靜態方式將 c + + 程式碼連結至 ATL 註冊機構程式碼。
ms.date: 09/03/2020
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: f08f7d9433ae1344c7a98a5c52502d03bad21e91
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609151"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>設定註冊機構程式碼的靜態連結 (c + + 僅) 

C + + 用戶端可以建立註冊機構的程式碼的靜態連結。 註冊機構的剖析器的靜態連結會將大約的大量新增至發行組建。

設定靜態連結的最簡單方式是假設您已 [`DECLARE_REGISTRY_RESOURCEID`](reference/registry-macros.md#declare_registry_resourceid) 在物件的宣告中指定。  (，則為 ATL 所使用的預設規格 ) 

## <a name="to-create-a-static-link-using-declare_registry_resourceid"></a>使用建立靜態連結 `DECLARE_REGISTRY_RESOURCEID`

1. **`/D _ATL_STATIC_REGISTRY`** **`/D _ATL_DLL`** 在 CL 命令列上指定 instead of。 如需詳細資訊，請參閱 [`/D`](../build/reference/d-preprocessor-definitions.md)。

1. 重新 編譯。

## <a name="see-also"></a>另請參閱

[註冊元件 (註冊機構) ](../atl/atl-registry-component-registrar.md)
