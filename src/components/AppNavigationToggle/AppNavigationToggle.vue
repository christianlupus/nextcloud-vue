<!--
 - @copyright Copyright (c) 2019 Christoph Wurst <christoph@winzerhof-wurst.at>
 -
 - @author Christoph Wurst <christoph@winzerhof-wurst.at>
 - @author John Molakvoæ <skjnldsv@protonmail.com>
 - @author Marco Ambrosini <marcoambrosini@icloud.com>
 -
 - @license GNU AGPL version 3 or any later version
 -
 - This program is free software: you can redistribute it and/or modify
 - it under the terms of the GNU Affero General Public License as
 - published by the Free Software Foundation, either version 3 of the
 - License, or (at your option) any later version.
 -
 - This program is distributed in the hope that it will be useful,
 - but WITHOUT ANY WARRANTY; without even the implied warranty of
 - MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 - GNU Affero General Public License for more details.
 -
 - You should have received a copy of the GNU Affero General Public License
 - along with this program. If not, see <http://www.gnu.org/licenses/>.
 -
 -->
<template>
	<Button class="app-navigation-toggle"
		type="tertiary"
		:aria-expanded="open ? 'true' : 'false'"
		:aria-label="label"
		aria-controls="app-navigation-vue"
		@click="toggleNavigation">
		<template #icon>
			<Menu :size="20" />
		</template>
	</Button>
</template>

<script>
import Button from '../Button/index.js'
import { t } from '../../l10n.js'

import Menu from 'vue-material-design-icons/Menu'

export default {
	name: 'AppNavigationToggle',

	components: {
		Button,
		Menu,
	},

	props: {
		open: {
			type: Boolean,
			required: true,
		},
	},

	computed: {
		label() {
			return this.open ? t('Close navigation') : t('Open navigation')
		},
	},
	methods: {
		toggleNavigation() {
			this.$emit('update:open', !this.open)
		},
	},
}
</script>

<style scoped lang="scss">

button.app-navigation-toggle {
	position: absolute;
	top: $topbar-margin;
	right: - $topbar-margin;
	margin-right: - $clickable-area;
}

</style>
