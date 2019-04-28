---
title: 了解自訂建置步驟和建置事件
ms.date: 11/04/2016
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
ms.openlocfilehash: fc12689148e3bf23c233e4656249625d1156f9a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314672"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>了解自訂建置步驟和建置事件

在 Visual C++ 開發環境中，有三種基本方式可自訂建置流程：

- **自訂建置步驟**

   自訂建置步驟是與專案建立關聯的建置規則。 自訂建置步驟可以指定要執行的命令列、任何其他輸入或輸出檔案，以及要顯示的訊息。 如需詳細資訊，請參閱[如何：將自訂建置步驟新增至 MSBuild 專案](how-to-add-a-custom-build-step-to-msbuild-projects.md)。

- **自訂建置工具**

   自訂建置工具是與一或多個檔案建立關聯的建置規則。 自訂建置步驟可以將輸入檔案傳遞至自訂建置工具，進而導致產生一或多個輸出檔案。 例如，MFC 應用程式中的說明檔是使用自訂建置工具所建置。 如需詳細資訊，請參閱[如何：將自訂建置工具新增至 MSBuild 專案](how-to-add-custom-build-tools-to-msbuild-projects.md)和[指定自訂建置工具](specifying-custom-build-tools.md)。

- **建置事件**

   建置事件可讓您自訂專案的組建。 有三種建置事件：*建置前*、*連結前*和*建置後*。 建置事件可讓您指定要在建置流程中的特定時間發生的動作。 例如，您可以使用建置事件，在專案完成建置後利用 **regsvr32.exe** 註冊一個檔案。 如需詳細資訊，請參閱[指定建置事件](specifying-build-events.md)。

[針對組建自訂進行疑難排解](troubleshooting-build-customizations.md)可協助您確保自訂建置步驟和建置事件如預期般執行。

自訂建置步驟或建置事件的輸出格式也可以增強工具的可用性。 如需詳細資訊，請參閱[格式化自訂建置步驟或建置事件的輸出](formatting-the-output-of-a-custom-build-step-or-build-event.md)。

建置事件和自訂建置步驟會依下列順序與其他建置步驟一起執行：

1. 建置前事件

2. 在個別檔案上自訂建置工具

3. MIDL

4. 資源編譯器

5. C/C++ 編譯器

6. 連結前事件

7. 連結器或管理員 (視情況)

8. 資訊清單工具

9. BSCMake

10. 在專案上自訂建置步驟

11. 建置後事件

`custom build step on the project` 和 `post-build event` 會在所有其他建置流程完成後依序執行。

## <a name="in-this-section"></a>本節內容

[指定自訂建置工具](specifying-custom-build-tools.md)<br/>
[指定建置事件](specifying-build-events.md)<br/>
[為組建自訂進行疑難排解](troubleshooting-build-customizations.md)<br/>
[設定自訂建置步驟或建置事件的輸出格式](formatting-the-output-of-a-custom-build-step-or-build-event.md)<br/>

## <a name="see-also"></a>另請參閱

[Visual Studio 專案 - C++](creating-and-managing-visual-cpp-projects.md)<br>
[建置命令和屬性的一般巨集](reference/common-macros-for-build-commands-and-properties.md)
