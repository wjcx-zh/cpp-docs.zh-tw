---
title: LINK 命令檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8934758d8aa406ea7b7c959b1fc535cde32195b1
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894677"
---
# <a name="link-command-files"></a>LINK 命令檔

您可以將命令列引數傳遞的命令檔形式的連結。 若要指定連結器的命令檔，請使用下列語法：

> **連結\@**  <em>commandfile&lt</em>

*Commandfile&lt*是文字檔案的名稱。 允許之間沒有空格或定位字元 at 符號 (**\@**) 和檔案名稱。 沒有任何預設的延伸模組;您必須指定完整的檔名，包括任何副檔名。 無法使用萬用字元。 您可以指定絕對或相對路徑與檔案名稱。 連結不會使用環境變數來搜尋此檔案。

在命令檔中，引數可以分隔的空格或定位字元 （因為在命令列上） 和新行字元。

您可以指定全部或部分命令列中的命令檔。 您可以使用多個 LINK 命令中的命令檔。 連結會接受命令檔案輸入，如同它已指定命令列上該位置中。 不可為巢狀命令檔。 連結回應命令檔案的內容，除非[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)指定選項。

## <a name="example"></a>範例

下列命令以建置 DLL 會傳入不同的命令檔中的物件檔案和程式庫的名稱，並會使用第三個命令的 /EXPORTS 選項指定的檔案：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)   
[連結器選項](../../build/reference/linker-options.md)