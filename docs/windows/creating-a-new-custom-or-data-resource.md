---
title: 建立新的自訂或資料資源 （c + +） |Microsoft Docs
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
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e2939c7f0a68401b4c1a8c43b5c6335a0acfcb3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403938"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>建立新的自訂或資料資源 （c + +）

您可以藉由將資源放在包含該檔案使用一般資源指令碼 (.rc) 檔語法，個別檔案中，然後以滑鼠右鍵按一下您的專案中建立新的自訂或資料資源**方案總管 中**，然後按一下**資源包括**快顯功能表。

### <a name="to-create-a-new-custom-or-data-resource"></a>建立新的自訂或資料資源

1. [建立 .rc 檔](../windows/how-to-create-a-resource-script-file.md) ，其中包含自訂或資料資源。

   您可以在 .rc 檔中，將自訂資料輸入為以 Null 結尾並加上引號的字串，或是十進位、十六進位或八進位格式的整數。

2. 在 **方案總管**中，以滑鼠右鍵按一下專案的 .rc 檔，然後按一下捷徑功能表中的 [資源包含]  。

3. 在 **編譯時間指示詞**方塊中，輸入`#include`陳述式，為包含您的自訂資源檔案的名稱。 例如: 

    ```cpp
    #include mydata.rc
    ```

   請確定您輸入的語法和拼字正確。 [編譯時期指示詞]  方塊的內容會完全依照您的輸入插入資源指令碼檔。

4. 按一下 [確定]  記錄您的變更。

另一種建立自訂資源的方式是匯入外部檔案作為自訂資源。 如需詳細資訊，請參閱 [匯入及匯出資源](../windows/how-to-import-and-export-resources.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[Binary Editor](binary-editor.md)