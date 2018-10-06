 <template>
    <div class="activity d-flex">
        <img width="50px" height="50px" class="rounded-circle mr-4" :src="item.userImg" alt="user">
        <div>
            <p><strong>{{ item.userName }}</strong><span class="gray"> {{ item.action }}</span><span> {{ item.subject }}</span></p>
            <span class="gray"><i class="far fa-clock"></i> {{ item.time }}</span>
        </div>
    </div>
</template>
<script>
export default {
    props: ['item']
}
</script>
