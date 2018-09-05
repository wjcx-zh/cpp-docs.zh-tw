---
title: 設定登錄器程式碼 （只有 c + +） 的靜態連結 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a66ca33aa95ea6ffd59860cf0a55e51266ef5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757694"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>設定登錄器程式碼 （只有 c + +） 的靜態連結

C + + 用戶端可以建立註冊機構的程式碼的靜態連結。 靜態連結的註冊機構的剖析器會將大約 5k，加入至發行組建。

若要設定靜態連結最簡單的方式會假設您已指定[DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid)物件的宣告中。 （這是使用 atl 的預設值規格）

### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>若要建立使用 DECLARE_REGISTRY_RESOURCEID 靜態連結

1. 指定[/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY`而不是 /D **_ATL_DLL**。

2. 重新編譯。

## <a name="see-also"></a>另請參閱

[登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)

