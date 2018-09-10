---
title: 符號名稱限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.name
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67527717319c4b571ff4b72b83d718c0ac149586
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313321"
---
# <a name="symbol-name-restrictions"></a>符號名稱限制

符號名稱限制如下所示：

- 所有[符號](../windows/symbols-resource-identifiers.md)必須是唯一的應用程式範圍內。 這可避免標頭檔中出現衝突的符號定義。

- 符號名稱的有效字元包括 A-Z、a-z、0-9 和底線 ( _ )。

- 符號名稱不能以數字開頭，而且僅限於 247 個字元。

- 符號名稱不能包含空格。

- 符號名稱不區分大小寫，但會保留第一個符號定義的大小寫。 定義符號的標頭檔是由資源編譯器/編輯器和 C++ 程式用來參考資源檔中定義的資源。 對於只有大小寫不同的兩個符號名稱，C++ 程式會將其視為兩個不同的符號，而資源編譯器/編輯器則會將這兩個名稱視為參考到單一符號。

   > [!NOTE]
   > 如果您未遵循下列的標準符號名稱配置 (ID*_[keyword])，而且您的符號名稱剛好與資源指令碼編譯器的已知關鍵字相同，則嘗試建置資源指令碼檔案會造成難以診斷的隨機錯誤產生。 若要避免這個問題，請遵守標準命名配置。

符號名稱具有描述性前置詞，指出它們所代表的資源或物件種類。 這些描述性前置詞的開頭為文字組合識別碼。 Microsoft Foundation Class 程式庫 (MFC) 使用下表所示的符號命名慣例。

|類別|前置詞|使用|
|--------------|------------|---------|
|資源|IDR_ IDD_ IDC_ IDI_ IDB_|快速鍵或功能表 (和相關或自訂資源) 對話方塊游標圖示點陣圖|
|功能表項目|ID_|Menu item|
|命令|ID_|命令|
|控制項和子視窗|IDC_|控制項|
|字串|IDS_|字串資料表中的字串|
|MFC|AFX_|保留給預先定義的 MFC 符號|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[變更符號或符號名稱 (識別碼)](../windows/changing-a-symbol-or-symbol-name-id.md)  
[符號值限制](../windows/symbol-value-restrictions.md)  
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)