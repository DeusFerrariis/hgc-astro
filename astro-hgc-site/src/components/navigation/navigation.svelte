<script context='module' lang='ts'>
    /**
     * @typedef {Object} NavItem - represents the data needed to construct
     * a navigation item
     * @property {string} path - represents the href to route to
     * @property {string} title - represents a label/title
     * @property {boolean} newTab - if true will open the nav item in another tab
     */
    export interface NavItem {
        path: string;
        title: string;
        newTab: boolean;
    }

    export const newNavItem = (
        path: string,
        title: string, 
        newTab: boolean = false): NavItem => {
            return {path, title, newTab}
    }

    export const navItemFromTitle = (
        title: string,
        newTab: boolean = false
    ): NavItem => {
        let path = '/' + title.toLowerCase() + '/'
        return {path, title, newTab}
    }

    export const newNav = {
        fromTitle: navItemFromTitle,
        default: newNavItem,
    }
</script>