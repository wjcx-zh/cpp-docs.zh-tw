---
title: OLE 通用對話方塊類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: 1854d19c540f5e3e64b47786f465a05213eced86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617797"
---
# <a name="ole-common-dialog-classes"></a>OLE 通用對話方塊類別

這些類別會透過實作幾個標準 OLE 對話方塊來處理一般 OLE 工作。 它們也針對 OLE 功能提供一致的使用者介面。

[COleDialog](reference/coledialog-class.md)<br/>
由架構用來包含所有 OLE 對話方塊的通用實作。 在使用者介面分類中的所有對話方塊類別都是衍生自這個基底類別。 `COleDialog` 無法直接使用。

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
顯示 [插入物件] 對話方塊，用於插入新的 OLE 連結的或內嵌的項目的標準使用者介面。

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
顯示 [選擇性貼上] 對話方塊，用於實作 [編輯選擇性貼上] 命令的標準使用者介面。

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
顯示 [編輯連結] 對話方塊中，用於修改連結項目的相關資訊的標準使用者介面。

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
顯示 [變更圖示] 對話方塊，用於變更與 OLE 內嵌或連結的項目關聯的圖示的標準使用者介面。

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
顯示 [轉換] 對話方塊，用於將 OLE 項目從一個類型轉換為另一個類型的標準使用者介面。

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
封裝 Windows 通用 OLE 屬性對話方塊。 [通用 OLE 屬性] 對話方塊可讓您使用與 Windows 標準一致的方式，輕鬆顯示和修改 OLE 文件項目的屬性。

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
顯示 [更新] 對話方塊，用於更新文件中的所有連結的標準使用者介面。 對話方塊包含進度指示器，以指出更新程序是如何接近完成。

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
顯示 [變更來源] 對話方塊，用於變更連結的目的地或來源的標準使用者介面。

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
顯示 [伺服器忙碌中] 和 [伺服器沒有回應] 對話方塊，用於處理呼叫忙碌的應用程式的標準使用者介面。 通常會透過 `COleMessageFilter` 實作自動顯示。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
