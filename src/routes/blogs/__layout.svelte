<div class="blog--container">
    <div class="blog--minor">
        <slot></slot>
    </div>
</div>

<style>
    .blog--container {
        max-width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .blog--minor {
        max-width: 67%;
    }
</style>