<script>
	import {page} from '$app/stores';

	const boardCode = $page.params['boardCode'];

	const boardNames = {
		notice: '공지',
		free1: '자유1',
		free2: '자유2'
	};

	const boardName = ((boardNames[boardCode] || '') + ' 게시판').trim();
</script>

<h1>{boardName}</h1>