---
title: 變更符號或符號名稱 (ID) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2fb5268ca23def96c31f724b93fbdf1c81c4a43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599691"
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>變更符號或符號名稱 (ID)

當您建立新的資源或資源物件時，開發環境會為其指派預設的符號名稱，例如 IDD_DIALOG1。 您可以使用[屬性 視窗](/visualstudio/ide/reference/properties-window)來變更預設的符號名稱，或變更已與資源相關聯的所有符號的名稱。

### <a name="to-change-a-resources-symbol-name"></a>變更資源的符號名稱

1. 在 [資源檢視](../windows/resource-view-window.md)，選取的資源。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **屬性** 視窗中，輸入新的符號名稱，或從現有的符號清單中選取**識別碼** 方塊中。

   如果您輸入新的符號名稱，它會自動指派值。

您可以使用[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)變更目前未指派給資源的符號名稱。 如需詳細資訊，請參閱 <<c0> [ 變更未指定的符號](../windows/changing-unassigned-symbols.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[符號名稱限制](../windows/symbol-name-restrictions.md)  
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)