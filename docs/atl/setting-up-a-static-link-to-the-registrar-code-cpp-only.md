---
title: 設定登錄器程式碼 （只有 c + +） 的靜態連結
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: b95bd17abca3237710956f3a1bf1b1d6fa9df51e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265323"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>設定登錄器程式碼 （只有 c + +） 的靜態連結

C + + 用戶端可以建立註冊機構的程式碼的靜態連結。 靜態連結的註冊機構的剖析器會將大約 5k，加入至發行組建。

若要設定靜態連結最簡單的方式會假設您已指定[DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid)物件的宣告中。 （這是使用 atl 的預設值規格）

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>若要建立使用 DECLARE_REGISTRY_RESOURCEID 靜態連結

1. 指定[/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_靜態\_登錄**而不是 **/D \_ATL\_DLL**。

1. 重新編譯。

## <a name="see-also"></a>另請參閱

[登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)
