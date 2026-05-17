<script>
    /** @type {import('./$types').PageProps} */
    let { data } = $props();
    import { page } from '$app/state';
    import { redirect } from '@sveltejs/kit';

    throw redirect(302, '/about');
</script>