<template>
	<VersionPicker>
	  <template #endBefore>
		<label>
		  <select class="version-selector" @change="handleVersionChange($event)">
			<option value="">-Select your Version-</option>
			<option v-for="version in versions" :value="version.url" :key="version.version">
			  {{ version.version }}
			</option>
		  </select>
		</label>
	  </template>
	</VersionPicker>
  </template>
  
  <script setup lang="ts">
  import VersionPicker from "vuepress-theme-hope/modules/navbar/components/Navbar.js";
  
  const docsBase: string = "https://docs.rundeck.com";
  
  // Include the last version in each minor release and "Cloud" as the latest
  const previousDocsVersions: string[] = [
	"Cloud",
	"5.8.0",
	"5.7.0",
	"5.6.1",
	"5.6.0",
	"5.5.0",
	"5.4.0",
	"5.3.0",
	"5.2.0",
	"5.1.2",
	"5.1.1",
	"5.1.0",
	"5.0.2",
	"5.0.1",
	"5.0.0",
	"4.17.6",
	"4.17.5",
	"4.17.4",
	"4.17.3",
	"4.17.2",
	"4.17.1",
	"4.17.0",
	"4.16.0",
	"4.15.0",
	"4.14.2",
	"4.14.1",
	"4.14.0",
	"4.13.0",
	"4.12.1",
	"4.12.0",
	"4.11.0",
	"4.10.2",
	"4.10.1",
	"4.10.0",
	"4.9.0",
	"4.8.0",
	"4.7.0",
	"4.6.1",
	"4.5.0",
	"4.4.0",
	"4.3.0",
	"4.2.0",
	"4.1.0",
	"4.0.0",
	"3.4.10",
	"3.3.9",
	"3.2.9",
	"3.1.3",
	"3.0.27",
	"2.11.14",
	"2.10.8",
	"2.9.2",
	"2.8.4",
	"2.7.3",
	"2.6.11",
	"2.5.3",
	"2.4.2",
	"2.3.2",
	"2.2.3",
	"2.1.3",
	"2.0.4",
  ];
  
  // Parse versions into a flat list
  const parseVersions = (versions: string[]): { version: string; url: string }[] => {
	return versions.map((version) => {
	  if (version === "Cloud") {
		return {
		  version: "Cloud",
		  url: `${docsBase}/docs/`,
		};
	  }
	  return {
		version,
		url: `${docsBase}/${version}`,
	  };
	});
  };
  
  // Reactive property for versions
  const versions = parseVersions(previousDocsVersions);
  
  // Handle version change
  const handleVersionChange = (event: Event): void => {
	const target = event.target as HTMLSelectElement;
	const selectedUrl = target.value;
	if (selectedUrl) {
	  document.location.href = selectedUrl;
	}
  };
  </script>