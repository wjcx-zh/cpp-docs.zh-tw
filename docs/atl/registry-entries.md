---
title: 登錄項目 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d74f458e28377dcc0bd7d6800cddc6e227c9f984
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751770"
---
# <a name="registry-entries"></a>登錄項目

DCOM 導入的應用程式識別碼 (Appid)，群組的一或多個 DCOM 物件在登錄中的集中式位置的組態選項的概念。 您可以指出名為物件的 CLSID 下值的 AppID 的值指定 AppID。

根據預設，ATL 產生的服務會使用 CLSID 的其 AppID 的 guid。 在下`HKEY_CLASSES_ROOT\AppID`，您可以指定 DCOM 特定項目。 一開始，有兩個項目：

- `LocalService`與相同服務的名稱值。 如果此值存在，它會使用而不是`LocalServer32`索引鍵下的 CLSID。

- `ServiceParameters`值等於`-Service`。 這個值會指定將在啟動時傳遞至服務的參數。 請注意，這些參數會傳遞至服務的`ServiceMain`函式，不`WinMain`。

任何 DCOM 服務也需要建立另一個索引鍵下的`HKEY_CLASSES_ROOT\AppID`。 此金鑰是相等的 EXE 名稱，做為交互參照，因為它包含 AppID 值指回 AppID 項目。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)

