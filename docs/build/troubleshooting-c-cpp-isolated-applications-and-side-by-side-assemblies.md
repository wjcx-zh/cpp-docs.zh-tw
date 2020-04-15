---
title: 疑難排解 C/C++ 隔離應用程式和並存組件
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 0dc8488acc90f1a38a4c0de0f052590ef4f398af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335445"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>疑難排解 C/C++ 隔離應用程式和並存組件

如果找不到相依程式庫，則載入 C/C++ 應用程式可能會失敗。 本文將說明為什麼無法載入 C/++ 應用Ｃ程式的一些常見原因，並建議解決問題的步驟。

如果應用程式無法載入，因為它具有在並存組件上指定相依性的資訊清單，且組件不會在可執行檔所在的相同的資料夾中安裝成私用組件，也不會在 %WINDIR%\WinSxS\ 資料夾的原生組件快取中安裝，則可能會顯示下列錯誤訊息，視您嘗試執行應用程式的 Windows 版本而定。

- 無法正確初始化應用程式 (0xc0000135)。

- 此應用程式無法啟動，因為應用程式組態不正確。 重新安裝應用程式可能可以解決這個問題。

- 系統無法執行指定的程式。

如果應用程式沒有清單,並且依賴於 Windows 在典型搜尋位置找不到的 DLL,可能會顯示類似於此消息的錯誤訊息:

- 此應用程式未啟動,因為找不到*所需的 DLL。* 重新安重新安裝應用程式可能可以解決這個問題。

如果將應用程式部署到沒有 Visual Studio 的電腦，且其損毀並顯示先前的類似錯誤訊息，請檢查這些情況：

1. 以[「瞭解視覺化應用程式的依賴性」中](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)所述的步驟C++ 。 相依性查核器可以顯示應用程式或 DLL 的大部分相依性。 如果您觀察到某些 Dll 會遺失，請在嘗試執行應用程式的電腦上安裝它們。

1. 作業系統載入器會使用應用程式資訊清單來載入應用程式所相依的組件。 資訊清單可以內嵌於二進位檔做為資源，或安裝為應用程式資料夾中的個別檔案。 要檢查清單是否嵌入到二進位檔案中,請在 Visual Studio 中打開二進位檔案,並在其資源清單中尋找RT_MANIFEST。 如果找不到嵌入的清單,請查看應用程式資料夾中的檔案,該檔名為類似<binary_name>。\<擴展>.清單。

1. 如果您的應用程式相依於並存組件，並且未出現資訊清單，您必須確定連結器可產生專案的資訊清單。 選取項目項目 **「項目屬性**」對話框中的 **「生成清單**」連結器選項。

1. 如果資訊清單內嵌於二進位檔，請確定 RT_MANIFEST 的識別碼對這種類型的二進位檔是正確的。 有關要使用的資源識別碼的詳細資訊,請參閱將並行[程式集用作資源 (Windows)](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource)。 如果資訊清單位於不同的檔案，請在 XML 編輯器或文字編輯器中開啟它。 有關部署清單和規則的詳細資訊,請參閱[清單](/windows/win32/sbscs/manifests)。

   > [!NOTE]
   > 如果出現內嵌資訊清單和個別的資訊清單檔案，作業系統載入器會使用內嵌資訊清單，並忽略個別的檔案。 不過，在 Windows XP 上的情況則相反，會使用不同的資訊清單檔案，而且會忽略內嵌資訊清單。

1. 我們建議您在每個 DLL 中內嵌資訊清單，因為在透過`LoadLibrary` 呼叫載入 DLL 時，會忽略外部資訊清單。 有關詳細資訊,請參閱[程式集清單](/windows/win32/SbsCs/assembly-manifests)。

1. 請檢查資訊清單中列舉的所有組件都會正確安裝在電腦上。 每個組件是依其名稱、版本號碼和處理器架構，在資訊清單中指定。 如果應用程式依賴於並行程式集,請檢查這些程式集是否正確安裝在電腦上,以便作業系統載入程式可以找到它們,如[程式集搜尋序列](/windows/win32/SbsCs/assembly-searching-sequence)中所述。 請記住，64 位元組件無法在 32 位元處理序中載入，而且無法在 32 位元作業系統上執行。

## <a name="example"></a>範例

假設我們有一個應用程式,appl.exe,這是通過使用視覺C++構建的。 應用程式資訊清單可能會內嵌在 appl.exe 做為二進位資源 RT_MANIFEST (具有等於 1 的識別碼)，或儲存為個別檔案 appl.exe.manifest。 此資訊清單的內容看起來像這樣：

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

對於作業系統載入器，此資訊清單假設 appl.exe 相依於名為 Fabrikam.SxS.Library 的組件，其版本為 2.0.20121.0，為針對 32 位元 x86 處理器架構所建置。 可將相依的並存組件安裝為共用組件或私用組件。

共用組件的組件資訊清單會安裝在 %WINDIR%\WinSxS\Manifests\ 資料夾中。 它會識別組件並列出其內容—也就是屬於組件的 DLL：

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

並行程式集還可以使用[發佈伺服器配置檔](/windows/win32/SbsCs/publisher-configuration-files)(也稱為策略檔)全域重定向應用程式和程式集,以使用並行程式集的一個版本,而不是同一程式集的另一個版本。 您可以在 %WINDIR%\WinSxS\Policies\ 資料夾中檢查共用組件的原則。 以下是範例原則檔案：

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">

   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <dependency>
      <dependentAssembly>
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>
      </dependentAssembly>
   </dependency>
</assembly>
```

這個原則檔案會指定要求此組件的 2.0.10000.0 版的任何應用程式或組件，改為使用 2.0.20121.0 版本，這是安裝在系統的目前版本。 若是在原則檔案中指定應用程式資訊清單所提及的組件版本，載入器會在 %WINDIR%\WinSxS\ 資料夾中，尋找資訊清單中指定的此組件版本，如果未安裝此版本，載入就會失敗。 而如果未安裝組件版本 2.0.20121.0，要求組件版本 2.0.10000.0 的應用程式載入會失敗。

不過，組件也可以安裝為安裝的應用程式資料夾中的私用並存組件。 如果作業系統找不到做為共用組件的組件，它會按下列順序，以私用組件方式尋找它：

1. 檢查應用程式資料夾中具有名稱程式集名稱\<>.manifest 的清單檔。 在此範例中，載入器會嘗試在 appl.exe 所在的資料夾中尋找 Fabrikam.SxS.Library.manifest。 如果找到資訊清單，則載入器會從應用程式資料夾載入組件。 如果找不到組件，載入就會失敗。

1. 嘗試打開包含\\appl.exe 的\>資料夾中<程序集名称\\= 資料夾,如果存在<程式集名稱\>= 存在,請嘗試在此資料夾\<中載入名稱程式集名稱>.manifest 的清單檔。 如果找到清單,載入程式將從\\\><程序集名称 + 資料夾中載入程式集。 如果找不到組件，載入就會失敗。

有關載入程式如何搜尋從屬程式集的詳細資訊,請參閱[程式集搜尋序列](/windows/win32/SbsCs/assembly-searching-sequence)。 如果載入器找不到做為私用組件的相依組件，載入會失敗並出現「系統無法執行指定的程式」訊息。 若要解決這個錯誤，請確定相依組件和屬於這些組件的 Dll，都做為私用或共用組件安裝在電腦上。

## <a name="see-also"></a>另請參閱

[隔離應用程式和並存組件的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[編譯 C/C++ 隔離應用程式和行程式集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
