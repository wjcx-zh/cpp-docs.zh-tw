---
title: 將專案從混合模式轉換為純中繼語言
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 05ece23e6d79fc399085099deebcde0aa4a92c64
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "70311941"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>將專案從混合模式轉換為純中繼語言

根據預設C++ ，所有 Visual CLR 專案都會連結到 C 執行時間程式庫。 因此，這些專案會分類為混合模式應用程式，因為它們會將機器碼與以 common language runtime （managed 程式碼）為目標的程式碼結合。 編譯時，它們會編譯成中繼語言（IL），也稱為 Microsoft 中繼語言（MSIL）。

> [!IMPORTANT]
> Visual Studio 2015 已淘汰，Visual Studio 2017 不再支援為 CLR 應用程式建立 **/clr： pure**或 **/clr： safe**程式碼。 如果您需要純或 safe 元件，建議您將應用程式轉譯為C#。

如果您使用的是支援 **/clr： pure**或C++ **/Clr： safe**的舊版 Microsoft 編譯器工具組，您可以使用這個程式將程式碼轉換成純 MSIL：

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>將混合模式應用程式轉換為純中繼語言

1. 移除[C 執行時間程式庫](../c-runtime-library/crt-library-features.md)（CRT）的連結：

   1. 在定義應用程式進入點的 .cpp 檔案中，將進入點變更為`Main()`。 使用`Main()`表示您的專案不會連結至 CRT。

   2. 在方案總管中，以滑鼠右鍵按一下您的專案，然後選取快捷方式功能表上的 [**屬性**]，以開啟應用程式的屬性頁。

   3. 在**連結器**的 [ **Advanced** project] 屬性頁中，選取**進入點**，然後在此欄位中輸入**Main** 。

   4. 針對主控台應用程式，請在**連結器**的 [**系統**專案] 屬性頁中選取 [**子系統**] 欄位，並將其變更為 **[主控台（/SUBSYSTEM：主控台）** ]。

      > [!NOTE]
      > 您不需要為 Windows Forms 應用程式設定此屬性，因為 [**子系統**] 欄位預設會設定為 [ **windows （/SUBSYSTEM： windows）** ]。

   5. 在*stdafx.h*中，將所有語句標記為`#include`批註。 例如，在主控台應用程式中：

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       -或-

       例如，在 Windows Forms 應用程式中：

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. 針對 Windows Forms 應用程式，在 form1.vb 中，將參考 Windows `#include`的語句標記為批註。 例如：

      ```cpp
      // #include <windows.h>
      ```

2. 將下列程式碼新增至*stdafx.h*：

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. 移除所有非受控類型：

   在適當的情況下，將非受控類型取代為[系統](/dotnet/api/system)命名空間中結構的參考。 下表列出常見的 managed 類型：

   |結構|描述|
   |---------------|-----------------|
   |[布林值](/dotnet/api/system.boolean)|表示布林值。|
   |[Byte](/dotnet/api/system.byte)|代表 8 位元不帶正負號的整數。|
   |[Char](/dotnet/api/system.char)|代表 Unicode 字元。|
   |[DateTime](/dotnet/api/system.datetime)|表示時間的瞬間，通常以一天的日期和時間表示。|
   |[Decimal](/dotnet/api/system.decimal)|代表十進位數值。|
   |[Double](/dotnet/api/system.double)|表示雙精度浮點數。|
   |[Guid](/dotnet/api/system.guid)|表示全域唯一識別項 (GUID)。|
   |[Int16](/dotnet/api/system.int16)|表示 16 位元帶正負號的整數。|
   |[Int32](/dotnet/api/system.int32)|表示 32 位元帶正負號的整數。|
   |[Int64](/dotnet/api/system.int64)|表示 64 位元帶正負號的整數。|
   |[IntPtr](/dotnet/api/system.intptr)|平台專用的類型，用以代表指標或控點。|
   |[SByte](/dotnet/api/system.byte)|代表 8 位元帶正負號的整數。|
   |[Single](/dotnet/api/system.single)|表示單精確度浮點數。|
   |[TimeSpan](/dotnet/api/system.timespan)|表示時間間隔。|
   |[UInt16](/dotnet/api/system.uint16)|表示 16 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UInt32](/dotnet/api/system.uint32)|表示 32 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UInt64](/dotnet/api/system.uint64)|表示 64 位元不帶正負號的整數 (Unsigned Integer)。|
   |[UIntPtr](/dotnet/api/system.uintptr)|平台專用的類型，用以代表指標或控點。|
   |[空位](/dotnet/api/system.void)|表示不會傳回值的方法。也就是說，此方法具有 void 傳回型別。|