<template>
    <div class="delete-account">
        <h1>Delete Your Account</h1>
        <p>
            Deleting your account is a permanent action and cannot be undone. This will
            result in the loss of all your data.
        </p>

        <!-- Form to confirm account deletion -->
        <form @submit.prevent="handleDelete">
            <div class="form-group">
                <label for="id">Account ID</label>
                <input type="text" v-model="id" placeholder="Enter your Account ID" required />
            </div>

            <div class="form-group">
                <label>
                    <input type="checkbox" v-model="confirmation" />
                    I understand that deleting my account is permanent.
                </label>
            </div>

            <button :disabled="!canDelete" type="submit" class="delete-button">
                Delete Account
            </button>
        </form>
    </div>
</template>


<script>
import axios from "axios";

export default {
    name: "DeleteView",
    data() {
        return {
            id: "",
            confirmation: false,
        };
    },
    computed: {
        canDelete() {
            return this.id.trim().length > 0 && this.confirmation;
        },
    },
    methods: {
        async handleDelete() {
            if (!this.canDelete) return;

            // Show confirmation dialog
            const userConfirmed = window.confirm(
                "Are you sure you want to delete your account? This action is permanent and cannot be undone."
            );

            // Proceed only if user confirms
            if (!userConfirmed) {
                alert("Account deletion canceled.");
                return;
            }

            try {
                const response = await axios.delete(
                    `https://backend.fego-rides.com/admin/delete-driver/${this.id}`
                );

                if (response.status === 200) {
                    alert("Your account has been deleted.");
                } else {
                    throw new Error("Failed to delete account.");
                }
            } catch (error) {
                console.error(error);
                alert("There was an issue deleting your account. Please try again.");
            }
        },
    }

};
</script>


<style scoped>
.delete-account {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #fff;
    font-family: Arial, sans-serif;
}

h1 {
    color: #d9534f;
    text-align: center;
}

p {
    font-size: 14px;
    color: #666;
    text-align: center;
}

.form-group {
    margin-bottom: 15px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
}

input[type="password"] {
    width: 100%;
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

input[type="checkbox"] {
    margin-right: 10px;
}

.delete-button {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    color: #fff;
    background-color: #d9534f;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.delete-button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}

.delete-button:hover:not(:disabled) {
    background-color: #c9302c;
}
</style>