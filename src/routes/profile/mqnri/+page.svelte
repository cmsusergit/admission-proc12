<script>
    import Profile from '$lib/component/profile/mqnri_profile.svelte'
    import { onMount } from 'svelte';
    export let data
    let profile
    onMount(()=>{
        profile=data?.profile
        console.log('----',profile);        
        if(data?.merit_number){
            let temp1=data?.merit_number.find(ob=>ob.category=='M')
            if(temp1){


                temp1.number=temp1.number>11?temp1.number+24:temp1.number
                profile['merit_number']=data?.merit_number
            }
            else{

                profile['merit_number']='-'
            }
        }
    })
    let uploadedFileList=data?.uploadedFileList
</script>
<div class="min-h-screen w-full">
    {#if data}
        {JSON.stringify(data?.profile)}
    {/if}
    <Profile profile={profile} uploadedFileList={uploadedFileList}></Profile>        
</div>
