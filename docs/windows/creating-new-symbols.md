---
title: 建立新的符號 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d1911a8bd8a7f3079497ec66ea1de59aff480a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604046"
---
# <a name="creating-new-symbols"></a>建立新的符號

當您開始新的專案時，您可能會發現先對應符號名稱，再建立將指派到的資源很方便。

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>使用資源符號對話方塊建立新符號

1. 在 [資源符號對話方塊](../windows/resource-symbols-dialog-box.md)，選擇**新增**。

2. 在 **名稱**方塊中，輸入符號名稱。

3. 接受指派的符號值。

   -或-

   在 **值**方塊中，輸入新值。

4. 按一下 **確定**新符號加入符號清單。

如果您輸入的符號名稱已經存在，此時會出現訊息方塊，說明已定義使用該名稱的符號。 您不能定義兩個或多個具有相同名稱的符號，但您可以定義具有相同數值的不同符號。 如需詳細資訊，請參閱 <<c0> [ 符號名稱限制](../windows/symbol-name-restrictions.md)並[符號值限制](../windows/symbol-value-restrictions.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[檢視資源符號](../windows/viewing-resource-symbols.md)  
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)