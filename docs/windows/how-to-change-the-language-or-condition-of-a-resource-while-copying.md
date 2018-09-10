---
title: 如何： 變更其語言或條件的資源時複製 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property [C++]
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26ec8987b22444c98bb7a88c791c4f941737ceae
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313308"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>如何： 變更其語言或條件的資源時複製 （c + +）

在資源中複製時，您可以變更其語言屬性或條件屬性，或兩者。

- 資源的語言就是識別資源的語言。 這由[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)來協助識別您要尋找的資源。 (不過，各語言的資源可能有與文字無關的差異，例如，只能在日文鍵盤上作用的快速鍵，或只適用於中文當地語系化組建的點陣圖等等)。

- 資源的條件是已定義的符號，用來識別使用此特定資源副本時的條件。

資源的語言和條件會顯示在 [工作區] 視窗中資源名稱後的括號中。 在此範例中，名為 IDD_AboutBox 的資源使用芬蘭文為其語言，而其條件是 XX33。

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>複製現有的資源並變更其語言或條件

1. 在.rc 檔中或在[資源檢視](../windows/resource-view-window.md) 視窗中，以滑鼠右鍵按一下您想要複製的資源。

2. 選擇**插入複本**從捷徑功能表。

3. 在 [**插入資源複本**] 對話方塊中：

   - 針對**語言**清單方塊中，選取的語言。

   - 在 **條件**方塊中，輸入條件。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：複製資源](../windows/how-to-copy-resources.md)  
[資源檔](../windows/resource-files-visual-studio.md)  
[資源編輯器](../windows/resource-editors.md)