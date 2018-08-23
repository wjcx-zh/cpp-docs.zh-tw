---
title: 變更符號&#39;s 數值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 748b45b93f6145a03d8cd9745b7b61e3482ec53d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603740"
---
# <a name="changing-a-symbol39s-numeric-value"></a>變更符號&#39;s 數值

針對單一資源相關聯的符號，您可以使用[屬性 視窗](/visualstudio/ide/reference/properties-window)變更符號值。 您可以使用[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)來變更目前未指派給資源的符號值。 如需詳細資訊，請參閱 <<c0> [ 變更未指定的符號](../windows/changing-unassigned-symbols.md)。

### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>變更指派給單一資源或物件的符號值

1. 在 [資源檢視](../windows/resource-view-window.md)，選取的資源。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **屬性**視窗中，輸入符號名稱，後面接著等號和整數**識別碼**方塊中，例如：

    ```
    IDC_EDITNAME=5100
    ```

下一次儲存專案時，會在符號標頭檔中儲存新值。 在 [ID] 方塊中，只有符號名稱保持可見狀態；在驗證之後，將不會顯示等號和值。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[符號值限制](../windows/symbol-value-restrictions.md)  
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)