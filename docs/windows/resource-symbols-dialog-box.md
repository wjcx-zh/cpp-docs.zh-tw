---
title: 資源符號對話方塊 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourcesymbols
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 09d34d0247f7fd039bca3ea9b643802856734926
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719299"
---
# <a name="resource-symbols-dialog-box-c"></a>資源符號對話方塊 （c + +）

**資源符號**c + + 對話方塊可讓您加入新的資源符號、 變更顯示，或請跳至原始程式碼中正在使用中位置的符號。

- **名稱**

   顯示的符號名稱。 如需詳細資訊，請參閱 <<c0> [ 符號名稱限制](../windows/symbol-name-restrictions.md)。

- **值**

   顯示符號的數值。 如需詳細資訊，請參閱 <<c0> [ 符號值限制](../windows/symbol-value-restrictions.md)。

- **使用中**

   選取時，指定符號正由一或多個資源使用。 一或多個資源會列在 [使用者] 方塊中。

- **顯示唯讀符號**

   選取時，顯示唯讀資源。 根據預設，**資源符號**對話方塊會顯示可修改的資源在資源指令碼檔案中，但選取這個選項，可修改的資源會以粗體文字以及唯讀資源會以純文字。

- **使用**

   使用在符號清單中選取的符號來顯示一或多個資源。 若要移到編輯器中指定的資源，請選取中的資源**藉由使用**方塊，然後按一下**檢視使用**。 如需詳細資訊，請參閱 <<c0> [ 開啟指定符號的資源編輯器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。

- **新增**

   會開啟**新符號** 對話方塊中，可讓您定義名稱並視需要新的符號資源識別項的值。 如需詳細資訊，請參閱 <<c0> [ 建立新的符號](../windows/creating-new-symbols.md)。

- **變更**

   會開啟**變更符號**對話方塊中，可讓您變更名稱或符號的值。 如果符號用於使用中的控制項或資源，只可以從對應的資源編輯器變更符號。 如需詳細資訊，請參閱 <<c0> [ 變更未指定的符號](../windows/changing-unassigned-symbols.md)。

- **檢視使用**

   開啟在對應資源編輯器中含有符號的資源。 如需詳細資訊，請參閱 <<c0> [ 開啟指定符號的資源編輯器](../windows/opening-the-resource-editor-for-a-given-symbol.md)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[檢視資源符號](../windows/viewing-resource-symbols.md)