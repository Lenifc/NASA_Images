<template>
    <div class="claimContainer">
        <h1>SPACER</h1>
        <p>
            Begin your jorney through our amazing galaxy, 
            and discover places you never even heard of.
        </p>
        <p>
            Type anything space-related to start.
        </p>
    </div>
</template>

<script>
export default {
    name: 'Claim'
}
</script>

<style lang="scss" scoped>
.claimContainer{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    max-width: 600px
}

h1{
    font-size: 50px;
}

p{
    margin-top: 20px;
    text-align: center;
    font-size: 14px;
}
</style>