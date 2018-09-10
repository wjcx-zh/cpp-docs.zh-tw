---
title: 編輯二進位資料 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- binary data
ms.assetid: 0fd429de-baf1-4871-b5e4-42bf868a3261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 050f52dface260da77f7290f47a9cbb204caaafe
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315454"
---
# <a name="editing-binary-data"></a>編輯二進位資料

### <a name="to-edit-a-resource-in-the-binary-editor"></a>若要編輯的二進位編輯器中的資源

1. 選取您想要編輯的位元組。

   ** 索引標籤**鍵將焦點移十六進位和 ASCII 區段之間**二進位**編輯器。 您可以使用**Page Up**並**Page down 鍵**金鑰一次移動一個螢幕的資源。

2. 輸入新值。

   值會立即變更十六進位和 ASCII 區段中，焦點會轉移至行中的下一個值。

   > [!NOTE]
   > **二進位**編輯器會接受變更的自動關閉編輯器時。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[Binary Editor](binary-editor.md)