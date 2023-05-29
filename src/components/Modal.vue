<template>
    <Transition name="modal">
        <div class="my-modal fixed inset-0 bg-[rgba(0,0,0,0.5)] pt-20 px-8 z-50" @click="$emit('close-modal')">
            <div
                class="modal-box bg-white sm:w-[70%] md:w-[60%] lg:w-[40%] mx-auto rounded-md border border-gray-300 transition duration-300">
                <div class="header">
                    <div class="close-btn w-9 h-9 p-1.5 -m-1.5"></div>
                    <slot name="modal-header"></slot>
                    <!-- <h2 class="text-2xl font-semibold">Modal Box</h2> -->
                    <div class="close-btn w-9 h-9 p-1.5 -m-1.5 rounded cursor-pointer hover:bg-gray-50 text-center"
                        @click="$emit('close-modal')">
                        <font-awesome-icon icon="fa-solid fa-xmark" class="text-xl" />
                    </div>
                </div>
                <div class="content">
                    <slot name="modal-content"></slot>
                    <!-- <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nesciunt, quis.</p> -->
                </div>
                <div class="footer">
                    <button class="btn btn-primary mr-3">Submit</button>
                    <button class="btn btn-secondary" @click="$emit('close-modal')">Cancel</button>
                </div>
            </div>
        </div>
    </Transition>
</template>
<style scoped>
.my-modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    padding: 5rem 2rem 3rem 2rem;
    z-index: 50;
}

.my-modal .modal-box {
    background: #fff;
    margin: auto;
    border: 1px solid #d1d5db;
    border-radius: 6px;
    transition: all 300ms;
}

.my-modal .header {
    padding: 12px;
    display: flex;
    justify-content: space-between;
    gap: 24px;
}

/* w-9 h-9 p-1.5 -m-1.5 rounded cursor-pointer hover:bg-gray-50 text-center */
.close-btn {
    width: 36px;
    height: 36px;
    padding: 6px;
    margin: -6px;
    border-radius: 4px;
    cursor: pointer;
    text-align: center;
}

.close-btn:hover {
    background-color: #f9fafb;
}

.my-modal .content,
.my-modal .footer {
    padding: 20px;
    border-top: 1px solid #d1d5db;
}

.my-modal .footer {
    text-align: right;
}

@media (min-width: 640px) {
    .my-modal .modal-box {
        width: 70%;
    }
}

@media (min-width: 768px) {
    .my-modal .modal-box {
        width: 60%;
    }
}

@media (min-width: 1024px) {
    .my-modal .modal-box {
        width: 40%;
    }
}
</style>