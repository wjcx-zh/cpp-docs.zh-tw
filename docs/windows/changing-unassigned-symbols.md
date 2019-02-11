---
title: 變更或刪除未指定的符號
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987010"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>變更或刪除未指定的符號

當您在[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)，您可以編輯或刪除現有的符號不是已指派給資源或物件。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="to-change-an-unassigned-symbol"></a>變更未指派的符號

1. 在 **名稱**，選取 未指派的符號，然後選擇**變更**。

1. 符號的名稱或值中提供的方塊中編輯**變更符號** 對話方塊。

   > [!NOTE]
   > 若要變更符號所*已*指派給資源或物件，您必須使用資源編輯器或**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 變更符號或符號名稱](../windows/changing-a-symbol-or-symbol-name-id.md)。

## <a name="to-delete-an-unassigned-unused-symbol"></a>刪除未指派 (未使用) 的符號

在 [資源符號對話方塊](../windows/resource-symbols-dialog-box.md)，選取您想要刪除，並選擇的符號**刪除**。

   > [!NOTE]
   > 在刪除資源檔中未使用的符號之前，請確定它未在程式的其他地方使用，或未由編譯時期包含的資源檔使用。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[檢視資源符號](../windows/viewing-resource-symbols.md)<br/>
[符號名稱限制](../windows/symbol-name-restrictions.md)<br/>
[符號值限制](../windows/symbol-value-restrictions.md)<br/>
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)