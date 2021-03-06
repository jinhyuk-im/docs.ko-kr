---
ms.openlocfilehash: 882c4c0455b7df538079ffe1b7d1d7ca8af1904a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606727"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>.NET 4.8에 대한 Windows Forms 콘트롤의 접근성 개선 사항

#### <a name="details"></a>설명

Windows Forms Framework는 Windows Forms 고객을 더욱 효과적으로 지원하도록 접근성 기술로 작업하는 방법을 지속적으로 개선합니다. 여기에는 다음과 같은 변경이 포함됩니다.

- 고대비 모드 중에 표시를 개선하기 위한 변경 내용
- 내레이터와 상호 작용의 변경 내용입니다.
- 액세스 가능한 계층 구조의 변경 내용(UI Automation 트리를 통한 탐색 개선).

#### <a name="suggestion"></a>제안 해결 방법

**이러한 변경을 옵트인 또는 옵트아웃하는 방법** 이러한 변경의 이점을 활용하려면 애플리케이션은 .NET Framework 4.8에서 실행되어야 합니다. 애플리케이션은 다음과 같은 방법으로 이러한 변경 내용을 옵트인할 수 있습니다.

- .NET Framework 4.8을 대상으로 다시 컴파일됩니다. 이러한 접근성 변경 내용은 .NET Framework 4.8을 대상으로 하는 Windows Forms 애플리케이션에서 기본적으로 활성화됩니다.
- .NET Framework 4.7.2 이전 버전을 대상으로 하며 다음 예제와 같이 app.config 파일의 `<runtime>` 섹션에 [AppContext 스위치](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)를 추가하고 이를 `false`로 설정하여 레거시 접근성 동작을 옵트아웃합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

.NET Framework 4.8에 추가된 접근성 기능을 옵트인하려면 .NET Framework 4.7.1 및 4.7.2의 접근성 기능도 옵트인해야 합니다. .NET Framework 4.8을 대상으로 하고 레거시 접근성 동작을 유지하려는 애플리케이션은 이 AppContext 스위치를 `true`로 명확하게 설정하여 레거시 접근성 기능 사용을 옵트인할 수 있습니다. 키보드 도구 설명 호출 지원을 사용하려면 `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` 줄을 AppContextSwitchOverrides 값에 추가해야 합니다.

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

이 기능을 사용하려면 앞에서 언급한 .NET Framework 4.7.1 - 4.8의 접근성 기능도 옵트인해야 합니다. 또한 접근성 기능을 옵트인하지 않고 도구 설명 표시 기능을 옵트인하면 이러한 기능에 처음 액세스할 때 런타임 <xref:System.NotSupportedException>이 throw됩니다. 예외 메시지는 키보드 도구 설명에서 수준 3의 접근성 개선을 사용하도록 요구함을 나타냅니다.

**고대비 테마에서 OS 정의 색 사용**

- 고대비 테마를 개선했습니다.

**향상된 내레이터 지원**

- 이제 내레이터는 <xref:System.Windows.Forms.DataGridViewCell>의 액세스 가능한 이름을 발표할 때 <xref:System.Windows.Forms.DataGridViewColumn>의 정렬 방향을 공지합니다.

**향상된 CheckedListBox 접근성 지원**

- <xref:System.Windows.Forms.CheckedListBox> 컨트롤에 대한 향상된 내레이터 지원. 키보드를 사용하여 <xref:System.Windows.Forms.CheckedListBox> 컨트롤로 이동할 때 내레이터는 <xref:System.Windows.Forms.CheckedListBox> 항목에 초점을 맞추고 이를 공지합니다.
- 이제 빈 CheckedListBox 컨트롤에 컨트롤이 집중되면 가상 첫 번째 항목에 대해 포커스 사각형이 그려집니다.

**향상된 ComboBox 접근성 지원**

- UI Automation 알림 및 기타 UI Automation 기능을 사용할 수 있는 기능이 있는 <xref:System.Windows.Forms.ComboBox> 컨트롤에 대한 UI Automation 지원을 사용할 수 있습니다.
**개선된 DataGridView 접근성 지원**

- UI Automation 알림 및 기타 UI Automation 기능을 사용할 수 있는 기능이 있는 <xref:System.Windows.Forms.DataGridView> 컨트롤에 대한 UI Automation 지원을 사용할 수 있습니다.
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> 또는 <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>에 해당하는 UI Automation 요소는 이제 해당 편집 셀의 자식입니다.

**향상된 LinkLabel 접근성 지원**

- 향상된 <xref:System.Windows.Forms.LinkLabel> 컨트롤 접근성: 내레이터는 해당 <xref:System.Windows.Forms.LinkLabel> 컨트롤이 비활성화된 경우 링크의 비활성화 상태를 알립니다.

**향상된 ProgressBar 접근성 지원**

- UI Automation 알림 및 기타 UI Automation 기능을 사용할 수 있는 기능이 있는 <xref:System.Windows.Forms.ProgressBar> 컨트롤에 대한 UI Automation 지원을 사용할 수 있습니다. 개발자는 이제 내레이터가 진행률을 표시하기 위해 알릴 수 있는 UI Automation 알림을 사용할 수 있습니다.
UI 자동화 알림 이벤트를 비롯하여 UI 자동화 이벤트 개요는 [UI 자동화 이벤트 개요](/windows/desktop/WinAuto/uiauto-eventsoverview)를 참조하세요.

**향상된 PropertyGrid 접근성 지원**

- UI Automation 알림 및 기타 UI Automation 기능을 사용할 수 있는 기능이 있는 <xref:System.Windows.Forms.PropertyGrid> 컨트롤에 대한 UI Automation 지원을 사용할 수 있습니다.
- 현재 편집된 속성에 해당하는 UI Automation 요소는 이제 해당 속성 항목 UI Automation 요소의 자식이 됩니다.
- 부모 <xref:System.Windows.Forms.PropertyGrid> 컨트롤이 범주 보기로 설정된 경우 UI Automation 속성 항목은 이제 해당 범주 요소의 자식이 됩니다.

**향상된 ToolStrip 지원**

- UI Automation 알림 및 기타 UI Automation 기능을 사용할 수 있는 기능이 있는 <xref:System.Windows.Forms.ToolStrip> 컨트롤에 대한 UI Automation 지원을 사용할 수 있습니다.
- <xref:System.Windows.Forms.ToolStrip> 항목을 통한 탐색 기능이 개선되었습니다.
- 항목 모드에서는 내레이터 포커스는 사라지지 않고 숨겨진 항목으로 이동하지 않습니다.

**개선된 시각적 표시**

- 이제 빈 <xref:System.Windows.Forms.CheckedListBox> 컨트롤은 포커스를 수신할 때 포커스 표시기를 표시합니다.
참고: UI 자동화 지원은 런타임의 컨트롤에 대해 활성화되지만 디자인 타임에는 사용되지 않습니다. UI 자동화 개요는 [UI Automation 개요](../../../../docs/framework/ui-automation/ui-automation-overview.md)를 참조하세요.

**키보드를 사용하여 컨트롤의 도구 설명 호출**

- 이제 컨트롤 도구 설명은 키보드로 집중하여 호출할 수 있습니다. 이 기능은 애플리케이션에 대해 명시적으로 사용하도록 설정해야 합니다( **&quot;이 변경 내용을 옵트인 또는 옵트아웃하는 방법&quot;** 섹션 참조).

| 이름    | 값       |
|:--------|:------------|
| Scope   | 주요함       |
| 버전 | 4.8         |
| 형식    | 대상 변경 |
